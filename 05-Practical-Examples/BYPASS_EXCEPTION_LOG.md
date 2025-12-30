### Exception Entry #2025-04
* **Date:** 12 Oct 2025
* **Target Release:** Hotfix v2.4.1 (Login Service)
* **Bypass:** Gate 3 (Full Automation Regression Suite)
* **Justification:** P0 incident—Production login is failing for 100% of Android users. Every hour of delay results in ~£12k lost revenue.
* **Risk:** High. Potential for regression in the 'Sign-up' flow which shares the same auth-module.
* **Mitigation:** 1. Manual 'Smoke Test' of Sign-up performed on two physical devices.
  2. Full Regression Suite scheduled to run automatically at 02:00 AM post-deploy.
  3. Manual Tester assigned for 9:00 AM verification next day.
* **Approved By:** Baskar (QA Lead) & Sarah J. (Product Owner)
