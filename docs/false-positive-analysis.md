# False-Positive Analysis Template

Create one copy per investigated event.

## Event
- Date/time:
- CRS version:
- Rule ID:
- Request path:
- Parameter / matched variable:
- Response status:
- Audit-log evidence:

## Assessment
- Why did the rule match?
- What legitimate application behavior was expected?
- Why is this classified as a false positive (or why is it still inconclusive)?

## Tuning
- Exclusion type:
- Scope (route, parameter and rule):
- Reason for selecting this scope:
- Rollback method:

## Validation
| Test | Expected | Actual | Evidence |
|---|---|---|---|
| Original benign request | Allowed | Pending | |
| Representative attack pattern | Detected/blocked as configured | Pending | |
| Unrelated benign request | Allowed | Pending | |

Do not mark an event as resolved until the retests are complete.
