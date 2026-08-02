# Deloitte Australia — Cyber Job Simulation
<img src = "https://github.com/niha-v/Cybersecurity-Job-Simulations/blob/main/deloitte_image.png" width ="400" >

**Role simulated:** Cyber security consultant, Deloitte Australia

Deloitte's simulation is framed around supporting a client through a live cyber security breach — investigating how private company information leaked and tracing the activity back to its source.
 
### Task 1 — Cyber Security Investigation: Daikibo Industrials
 
**Scenario:** A major news publication revealed sensitive private information about Daikibo Industrials, a client whose assembly lines had stopped due to a production issue that threatened downstream supply chains. Daikibo suspected the security of their new telemetry status board had been breached.
 
**My job:**
1. Determine whether the alleged breach could have happened from an attacker on the open internet directly — with no access to Daikibo's VPN
2. Inspect a `web_requests.log` file covering the window during which the alleged attack had to have occurred

**Approach:**
- Parsed a log file structured as per-IP blocks, each listing that device's requests to Daikibo's intranet-hosted telemetry dashboard, sorted by time
- Looked for the expected legitimate pattern — login → dashboard resource requests (styles/scripts/images) → API requests for machine status — and flagged sequences that deviated from it
- Identified requests hitting the API at suspiciously exact, fixed time intervals, inconsistent with manual page refreshes (the dashboard has no auto-polling, so real users must manually refresh to get updated data)
- Traced the flagged automated-looking requests back to a specific user ID within the logs, and used that finding — combined with the internal/static nature of Daikibo's IP addressing — to assess whether the breach was consistent with an external internet-based attacker or an internal account

### Skills demonstrated
`log analysis` · `incident investigation` · `anomaly detection` · `client-facing security consulting` · `attack source identification`
 


