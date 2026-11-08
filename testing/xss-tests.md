# XSS Pattern Detection Test Plan

Use only the local Juice Shop instance.

Example request pattern:

```bash
curl -i --get --data-urlencode "q=<script>alert(1)</script>" http://127.0.0.1:8080/
```

A WAF may detect, transform, or pass a request depending on the endpoint, encoding, rules and configuration. Record the actual outcome; do not claim a block based only on the payload being sent.

Capture the exact request, response, matching CRS rule ID, audit event and engine mode.
