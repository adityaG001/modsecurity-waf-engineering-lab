# CRS Rule Tuning

**Status:** Planned.

## Investigation workflow
1. Reproduce the event with the exact request.
2. Inspect the ModSecurity audit event.
3. Identify the CRS rule ID, matched variable, message and anomaly score.
4. Decide whether the request is malicious, benign or inconclusive.
5. If benign, create the narrowest possible exclusion (specific rule and parameter/route where supported).
6. Retest the legitimate request.
7. Retest representative malicious requests to ensure protection remains.
8. Document the reason, scope and rollback procedure.

## Tuning principles
- Do not disable an entire rule because one request was blocked.
- Do not lower detection globally to hide a false positive.
- Keep exclusions version-controlled and explain each one.
- Re-test after CRS updates because rule behavior can change.

Record the CRS version, rule ID, endpoint, parameter, evidence reference and before/after result.
