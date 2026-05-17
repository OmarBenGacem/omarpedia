Overview table

| **Workload/Set** | **Description**                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Deployment**   | Used for deploying stateless applications                                                                                                      |
| **Replica Set**  | This is specifically used to ensure a specific number of pods exist, these are only used within deployments                                    |
| **Stateful Set** | These are collections of pods that require unique identities and persistent storage such as a databases and log managers.                      |
| **Dameon Set**   | A dameon set is a pod that runs identically across all nodes, an example is like Fluentbit agents and Prometheus monitors                      |
| **Job**          | These are used for one off finite tasks that run to completion. Examples are periodic cleanups, automated syncs and responding to API requests |
| **Cron Job**     | Running recurring and scheduled tasks such as a daily report or periodic cleanup                                                               |
%% Begin Waypoint %%
- [[Cron Jobs]]
- [[Dameon Sets]]
- [[Deployments]]
- [[Jobs]]
- [[Replica Sets]]
- [[Stateful Sets]]

%% End Waypoint %%
