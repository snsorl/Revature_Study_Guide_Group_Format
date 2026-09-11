# SPL Practice Queries — `simulation.log`

Based on your uploaded log (500 simulated transactions: 317 INFO, 131 WARN, 57 ERROR).
All queries assume `source="simulation.log"` and that `level`, `timestamp`, and `message`
are already available as fields (as shown in your own working examples).

---

## Beginner

**1. Count of each log grouped by log level**
```spl
source="simulation.log" | stats count by level
```

**2. Get the error logs to see their messages**
```spl
source="simulation.log" level=ERROR | table message
```

**3. Same error messages, plus timestamp**
```spl
source="simulation.log" level=ERROR | table timestamp message
```

**4. Log levels over time (you'll see spikes when you switch to Visualization)**
```spl
source="simulation.log" | timechart count by level
```

**5. Total number of log events in the file**
```spl
source="simulation.log" | stats count
```

**6. Get all WARN (flagged-for-review) events**
```spl
source="simulation.log" level=WARN | table timestamp message
```

**7. Show the first 20 events as they appear in the file**
```spl
source="simulation.log" | head 20
```

**8. Show the 10 most recent events**
```spl
source="simulation.log" | sort -_time | head 10
```

**9. Count events by level, worst (or most frequent) first**
```spl
source="simulation.log" | stats count by level | sort -count
```

**10. List the distinct log levels present in this file**
```spl
source="simulation.log" | dedup level | table level
```

**11. Keep only the first WARN and first ERROR event (one of each)**
```spl
source="simulation.log" (level=WARN OR level=ERROR) | dedup level
```

**12. Find only successful transactions using a keyword search**
```spl
source="simulation.log" "processed successfully" | table timestamp message
```

---

## Intermediate

**13. Extract the iteration number out of the message text**
```spl
source="simulation.log"
| rex field=message "Iteration (?<iteration>\d+):"
| table iteration level message
```
> `rex` isn't in your reference doc's core command list yet, but it's the tool you reach for
> whenever the field you want is buried inside free text rather than already broken out.

**14. Extract the reason for each failed (ERROR) transaction**
```spl
source="simulation.log" level=ERROR
| rex field=message "Reason: (?<reason>.+)"
| table timestamp reason
```

**15. Count failures by reason, most common first**
```spl
source="simulation.log" level=ERROR
| rex field=message "Reason: (?<reason>.+)"
| stats count by reason
| sort -count
```

**16. Find the single most common failure reason**
```spl
source="simulation.log" level=ERROR
| rex field=message "Reason: (?<reason>.+)"
| stats count by reason
| sort -count
| head 1
```

**17. Extract the dollar amount from successful transactions**
```spl
source="simulation.log" "processed successfully"
| rex field=message "Amount: \$(?<amount>\d+)"
| eval amount=tonumber(amount)
| table timestamp amount
```

**18. Average and max transaction amount for successful transactions**
```spl
source="simulation.log" "processed successfully"
| rex field=message "Amount: \$(?<amount>\d+)"
| eval amount=tonumber(amount)
| stats avg(amount) as avg_amount, max(amount) as max_amount, min(amount) as min_amount
```

**19. Extract the threshold-exceeding amount from flagged (WARN) transactions**
```spl
source="simulation.log" level=WARN
| rex field=message "threshold: \$(?<threshold_amount>\d+)"
| eval threshold_amount=tonumber(threshold_amount)
| table timestamp threshold_amount
```

**20. Find the 5 largest flagged (WARN) transaction amounts**
```spl
source="simulation.log" level=WARN
| rex field=message "threshold: \$(?<threshold_amount>\d+)"
| eval threshold_amount=tonumber(threshold_amount)
| sort -threshold_amount
| head 5
| table timestamp threshold_amount
```

**21. Calculate the overall error rate as a percentage**
```spl
source="simulation.log"
| stats count as total, sum(eval(if(level="ERROR", 1, 0))) as errors
| eval error_rate_pct = round((errors / total) * 100, 2)
| table total errors error_rate_pct
```

**22. Label every event as pass/fail/review using `eval` + `case()`, then count**
```spl
source="simulation.log"
| eval outcome = case(
    level="INFO", "pass",
    level="WARN", "review",
    level="ERROR", "fail",
    true(), "unknown"
  )
| stats count by outcome
| sort -count
```

**23. Only show flagged transactions over $12,000 using `where`**
```spl
source="simulation.log" level=WARN
| rex field=message "threshold: \$(?<threshold_amount>\d+)"
| eval threshold_amount=tonumber(threshold_amount)
| where threshold_amount > 12000
| table timestamp threshold_amount
```

**24. Use `top` to quickly see the most common level without writing `stats`+`sort`**
```spl
source="simulation.log" | top level
```

**25. Find the range of iteration numbers actually present (sanity check on data completeness)**
```spl
source="simulation.log"
| rex field=message "Iteration (?<iteration>\d+):"
| eval iteration=tonumber(iteration)
| stats min(iteration) as first_iteration, max(iteration) as last_iteration, count
```

---

## Tips as you work through these

- Run 1–12 first — they only use fields you already have (`level`, `timestamp`, `message`).
- Queries 13+ introduce `rex`, which uses a regex with a named group `(?<name>...)` to pull a
  new field out of existing text. If a rex query returns blank fields, check the `level` filter
  matches the message shape you're targeting (e.g. `Amount: $` only appears on INFO messages).
- After any `stats` command, remember you're working with summary rows, not raw events — you'll
  lose access to `message`/`timestamp` unless you brought them along via `by` or `values()`.
- For query 4, switch to the **Visualization** tab and pick a line or column chart to see the
  level breakdown over time.
