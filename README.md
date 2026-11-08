# ModSecurity WAF Engineering Lab

**Owner:** [adityaG001](https://github.com/adityaG001)  
**Status:** `Planned` — deployment, tuning and test evidence will be added as the lab is completed.

A hands-on Web Application Firewall lab using ModSecurity and the OWASP Core Rule Set (CRS) to protect an intentionally vulnerable application in an isolated environment.

## Objectives
- Deploy ModSecurity + OWASP CRS as a reverse proxy.
- Place OWASP Juice Shop behind the WAF without publishing the backend port.
- Compare `DetectionOnly` and blocking (`On`) modes.
- Inspect audit events and CRS rule IDs.
- Investigate false positives and apply narrowly scoped exclusions.
- Validate that tuning does not silently weaken unrelated protections.

## Architecture

```text
Kali / browser
      |
      v
ModSecurity + OWASP CRS (WAF reverse proxy)
      |
      v
OWASP Juice Shop (backend, internal Docker network)
```

## Components
| Component | Purpose |
|---|---|
| ModSecurity | WAF engine |
| OWASP CRS | Generic attack detection rules |
| Docker Compose | Reproducible deployment |
| OWASP Juice Shop | Intentionally vulnerable test application |
| curl / browser | Controlled request generation |

## Quick start
1. Review [`docs/architecture.md`](docs/architecture.md) and [`docs/deployment.md`](docs/deployment.md).
2. Start the stack with `docker compose up -d`.
3. Verify that the WAF is the only published application entry point.
4. Test benign requests first.
5. Begin in detection-only mode; inspect logs before enabling blocking.
6. Record actual rule IDs, response codes and outcomes in `testing/`.

## Safety
Run only on systems you own or are authorized to test. Keep Juice Shop isolated and do not publish it directly to the Internet. Bind the lab to localhost or an isolated lab interface as appropriate. Never use real user data.

## Evidence policy
No attack-detection, blocking or false-positive claims are made until the test has been executed and the evidence recorded.

## References
- [OWASP CRS documentation](https://coreruleset.org/docs/)
- [Official CRS Docker repository](https://github.com/coreruleset/modsecurity-crs-docker)
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [ModSecurity documentation](https://github.com/owasp-modsecurity/ModSecurity)
