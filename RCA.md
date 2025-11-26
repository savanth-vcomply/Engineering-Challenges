# 🚨 Root Cause Analysis (RCA)

**Incident Title:**  TaskHub API Outage — Tasks Not Loading
**Date / Time (Start–End):**  24 Nov 2025, 15:10 - 15:55
**Severity:**  Critical
**Services Impacted:** TaskHub API Service 

---

## 1. Summary
Yesterday, between 15:10 IST and 15:55 IST, the TaskHub dashboard page failed to load tasks for all users across the platform. Issue was resolved at 15:15 IST after correcting an incorrect configuration.


## 2. Impact
- Services effected: **API service**
- Percentage of users impacted: **100%**
- Average number of failed requests:  **500 RPM**
- Data loss: **Nil**



## 3. What Went Wrong
A **missing AppConfig flag** required by the API service to fetch tasks caused the FetchTasks API to fail and return a **500** error.


## 4. Root Cause Analysis (The Real WHY)
- The issue occurred because of a missing flag in the AppConfig(CacheProviderEnabled) during the deployment of a new feature
- This flag is used by the FetchTasks API in API service causing it to occur a run-time error while executing the logic.
- The failure went unnoticed initially because of missing alert on increasing error rate during a certain period

### Breakdown
#### 4.1 Direct Cause
Missing a **mandatory** flag in the AppConfig during deployment

#### 4.2 System Gap
**No validator** for application config during the release or build pipeline

#### 4.3 Detection Gap
**No alert** for increasing API error rate



## 5. Resolution
The following actions are taken to fix and restore the service:
-  Reverted the AppConfig to its previous stable version
-  Build the application with the modified AppConfig
-  Validated the FetchTasks API with the latest build 
-  Deployed the API Service with the latest build

## 6. Timeline (IST)
| Time | Event |
|------|--------|
| 15:10 | Deployment occured |
| 15:15 | Issue detected |
| 15:30 | Root cause identified |
| 15:45 | Build completed with fix |
| 15:55 | API Service restored |



## 7. Preventive Actions (Long-Term Fixes)
The following action items are suggested to avoid this kind of issues:
-  Add a config validator in the build pipleline 
-  Build should fail in case of missing or incorrect configs
-  Add alerting mechanism for increasing API error rate

