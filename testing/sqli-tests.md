# SQL Injection Detection Test Plan

Use only the local Juice Shop instance.

Example request pattern (URL encoding may be needed):

```bash
curl -i --get --data-urlencode "q=' OR 1=1--" http://127.0.0.1:8080/
```

This is a detection test, not a guarantee that a specific CRS rule will match. Record:
- Exact request
- CRS rule ID and message, if any
- Anomaly score, if present
- HTTP response
- Engine mode
- Audit-log evidence
- Interpretation and retest result
