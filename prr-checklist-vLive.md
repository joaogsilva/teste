# Production Readiness Review Checklist Template

## Reviewers
The reviewers should be filled in as one of the steps of the checklist below.
If a reviewer in the "Mandatory" section is not allocated, please add the reason.

### Mandatory
- Product Owner: {+ reviewer name +}
- Release Manager: {+ reviewer name +}
- Technical Leader: {+ reviewer name +}

## Checklist
This checklist contains points that must be satisfied according to the criticality of the microservice, which can be classified as low, medium, high or critical.

| i | Item         | Item Description                                                                                                                                                 | Not satisfied | Partially satisfied | Totally satisfied | Not applicable |
| - | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ------------------- | ----------------- | -------------- |
| 1 | Architecture | Are there capacity planning for infrastructure and operations? (data, cost, users,  network consumption, TPS, batchs, etc)                                       |               |                     |                   |                |
| 2 | Monitoring   | Is the service logging in JSON format and are logs and tracing forwarded to Datadog?                                                                             |               |                     |                   |                |
| 3 | Monitoring   | All architecture components are monitored to ensure business continuity and application reliability?                                                             |               |                     |                   |                |
| 4 | Monitoring   | Are there business metrics that should be monitored to ensure business continuity and application reliability?                                                   |               |                     |                   |                |
| 5 | Monitoring   | Do we have alerts that are triggered when any architecture component fails?                                                                                      |               |                     |                   |                |
| 6 | Reliability  | Is there a rollback plan?                                                                                                                                        |               |                     |                   |                |
| 7 | Reliability  | Do the on-call rotations responsible for this service have access to it and it's documentation?                                                                  |               |                     |                   |                |
| 8 | Reliability  | For all dependencies external and internal to the service, are there backups, alternatives, fallbacks, defensive caching, retry and back-off strategies defined? |               |                     |                   |                |

### Risk Calculate
The risk is calculated based on the formula below and it is measured to identify risks in production environments.

| Item Weights |
| ------------ |
| 0, 1 or 2    |

| Calculation                                                      |
| ---------------------------------------------------------------- |
| Risk = \[(a0 \* t0) + (a1 \* t1) + (ai \* ti) + ... + (an \* tn)\]/n |

*Where:*

*i: item index*

*ai: item answer based on item weight (0 if "Not satisfied"; 1 if "Partially satisfied"; 2 if "Totally satisfied")*

*ti: item answer multiplicator (1 if "Not satisfied"; 0,5 if "Partially satisfied"; 0 if "Totally satisfied")*

*n: number of applicable items*