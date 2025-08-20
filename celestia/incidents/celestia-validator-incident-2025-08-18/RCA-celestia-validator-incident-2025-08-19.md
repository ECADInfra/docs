# RCA: Celestia Validator Consensus Issues (2025-08-19)
---

Author: Gino Imbrailo
RCA Team: Jev Bjorsell, Gino Imbrailo

## 1. Executive Summary
   - **Incident Description**: The ECAD Infra team detected consensus performance degradation affecting our Celestia validator starting at 23:15 UTC on August 18, 2025. The incident was characterized by sustained missed blocks (~1 block every 2 minutes) and abnormally high consensus "Timed out" message durations. Grafana metrics showed up to 47 missing validators across the network, confirming this was not an isolated infrastructure issue. The validator experienced consistent 10-12.5 second block times compared to the normal ~5 seconds. A planned service restart at 00:30 UTC did not resolve the issue, and the incident continued until natural recovery at 02:43 UTC.
   - **Resolution Summary**: The incident resolved naturally without local intervention at 02:43 UTC on August 19, 2025. No infrastructure changes or manual actions were required. The resolution coincided with broader network improvement, confirming this was a distributed consensus coordination issue affecting multiple validators simultaneously.

## 2. Incident Details
- **Services Affected**: Celestia Mainnet Validator
- **Users Impacted**: Internal users, validator team
- **Incident Severity**: Critical

## 3. Timeline of Events
- **Incident Start:**        2025-08-18 23:15 UTC
- **Time of Detection:**     2025-08-18 23:15 UTC (Prometheus alerts)
- **Planned Restart:**       2025-08-19 00:30 UTC
- **Service Recovery:**      2025-08-19 00:35 UTC
- **Continued Degradation:** 2025-08-19 00:35-02:43 UTC
- **Natural Resolution:**    2025-08-19 02:43 UTC
- **Stable Operation:**      2025-08-19 02:50 UTC onwards

## 4. Technical Analysis
   - **Root Cause**: 
       * Grafana metrics confirmed 47 missing validators at peak (00:18 UTC), representing a substantial portion of the network.
       * Consensus "Timed out" message analysis revealed abnormally high and consistent duration values (~4150-4170ms) with no variation, compared to normal operation showing healthy variation (1000ms to 4169ms). The correlation between these high durations and missed blocks suggests potential consensus timing coordination issues.
       * Block time metrics showed sustained spikes of 10-12.5 seconds throughout the incident period, compared to baseline ~5 seconds.
       * Infrastructure assessment confirmed no local issues: stable peer connections (10 peers), no disk/memory/CPU problems, no network connectivity issues.
   - **Contributing Factors**: 
        * The incident occurred during a period of distributed consensus performance issues, as evidenced by synchronized block time spikes across multiple validators.
        * Natural resolution timing suggests external network coordination improvements rather than local infrastructure recovery.
        * The planned service restart did not resolve the issue, further confirming the distributed nature of the problem.

## 5. Evidence from Monitoring
   - **Grafana Dashboard Metrics**:
      * **Missing Validators**: Peak of 47 missing validators at 00:18 UTC
      * **Block Times**: Consistently 10-12.5 seconds (vs normal ~5 seconds)
      * **Missed Blocks**: Sustained 2-6 missed blocks per 10-minute period
      * **Connected Peers**: Stable at 10 peers (no connectivity issues)
   - **Grafana Dashboard Screenshots**:
      * [Dashboard Overview - Incident Period](grafana-dashboard-1.png)
      * [Dashboard Details - Missing Validators](grafana-dashboard-2.png)
   - **Log Analysis**:
      * 2,374 consensus "Timed out" messages over ~2 hours 13 minutes
      * Duration pattern: Consistently high (~4150-4170ms) with no variation
      * 99% RoundStepNewHeight consensus step
      * No infrastructure errors detected

## 6. Corrective and Preventive Measures
   - **Immediate Actions Taken**:
      * Comprehensive monitoring confirmed distributed issue scope
      * Infrastructure assessment prevented unnecessary interventions
      * Documented incident patterns for future distributed issue identification
   - **Short-term Corrective Actions**: 
      * Enhanced monitoring for consensus block time spikes
      * Automated detection for distributed consensus issues
      * Baseline documentation of normal operation patterns

## 7. Lessons Learned
   - **What Went Well**: 
      * Prometheus metrics enabled early detection and accurate problem scoping
      * Data-driven response prevented unnecessary infrastructure changes
      * Comprehensive evidence collection supported distributed issue confirmation
   - **What Could Be Improved**:
      * Distributed consensus issue detection could be automated
      * Community communication channels for coordinated incident response
      * Predictive monitoring for consensus timing coordination issues

## 8. Additional Resources
For comprehensive incident analysis including detailed log files, technical analysis, and community recommendations, see the full incident report and supporting documentation in our repository:
- **Full Incident Report**: [celestia-validator-incident-2025-08-18.md](https://github.com/ECADInfra/docs/blob/main/celestia/incidents/celestia-validator-incident-2025-08-18/celestia-validator-incident-2025-08-18.md)
- **Grafana Dashboard Screenshots**: [Dashboard Overview](grafana-dashboard-1.png) and [Missing Validators Detail](grafana-dashboard-2.png)
- **Sanitized Log Files**: [celestia-second-incident-sanitized.log](https://github.com/ECADInfra/docs/blob/main/celestia/incidents/celestia-validator-incident-2025-08-18/celestia-second-incident-sanitized.log)
- **Error Analysis**: [celestia-errors-categorized.log](https://github.com/ECADInfra/docs/blob/main/celestia/incidents/celestia-validator-incident-2025-08-18/celestia-errors-categorized.log) and [celestia-errors-summary.log](https://github.com/ECADInfra/docs/blob/main/celestia/incidents/celestia-validator-incident-2025-08-18/celestia-errors-summary.log)
- **Repository Location**: [docs/celestia/incidents/celestia-validator-incident-2025-08-18/](https://github.com/ECADInfra/docs/tree/main/celestia/incidents/celestia-validator-incident-2025-08-18)
