# Backgrounder load balancing

**Backgrounder Load Balancing in Tableau**

**Introduction**
Backgrounder processes handle asynchronous server tasks. These tasks include extract refreshes, subscriptions, and data-driven alerts. Load balancing distributes these tasks across multiple Backgrounder processes. This prevents any single process from becoming overloaded. The goal is to improve job throughput and system reliability.

**How Backgrounder Load Balancing Works**

**Process Architecture**
*   A Tableau Server cluster can have multiple Backgrounder processes.
*   These processes run on one or more nodes in the cluster.
*   Each Backgrounder process picks jobs from a shared queue.

**Job Distribution Method**
*   Jobs enter a central queue managed by the Application Server (VizPortal).
*   Each Backgrounder polls the queue for available jobs.
*   The default distribution uses a "pull" model. An idle Backgrounder takes the next job from the queue.
*   This method provides basic, even distribution across available processes.

**Queue Priority**
The queue prioritizes jobs by type.
1.  **High Priority**: Tasks for user-facing requests (e.g., "View Now" for an extract).
2.  **Normal Priority**: Scheduled extract refreshes and most subscriptions.
3.  **Low Priority**: Some maintenance and system tasks.
*   Backgrounders always take the highest priority job available.

**Benefits of Load Balancing**

**Increased Throughput**
*   Multiple Backgrounders can execute jobs simultaneously.
*   This reduces wait times for tasks during peak periods.

**Improved Reliability**
*   If one Backgrounder process fails, others continue processing jobs.
*   Failed jobs can be retried on another available process.

**Resource Optimization**
*   Workloads distribute across server hardware resources (CPU, memory).
*   Prevents a single node from being overwhelmed by intensive extract jobs.

**Configuration and Management**

**Initial Setup**
*   Add Backgrounder processes during initial Tableau Server installation or through node addition.
*   For Tableau Cloud, this is managed by Salesforce. Customers cannot add or remove Backgrounders directly.

**On-Premises Configuration**
*   Use the Tableau Services Manager (TSM) CLI or web interface.
*   Add a Backgrounder role to a node: `tsm topology set-role -r backgrounder -n <node-id>`
*   Apply pending changes: `tsm pending-changes apply`

**Process Tuning**
*   Control the number of job "slots" per Backgrounder.
    *   A slot allows one job to run.
    *   Default is 1 slot per Backgrounder process.
    *   Increasing slots lets a single process run multiple concurrent jobs.
*   Adjust via TSM: Set the `backgrounder.count` configuration key.

**Monitoring Backgrounder Performance**

**Use Admin Views and Status Pages**
*   **Background Tasks View**: Shows jobs in the queue, currently running, and recently completed.
*   **Status Page**: Lists all Backgrounder processes and their current state (Active, Busy, Idle).
*   **System Performance Views**: Monitor CPU and memory usage on nodes hosting Backgrounders.

**Key Metrics to Watch**
*   **Queue Wait Time**: How long jobs sit in the queue before a Backgrounder picks them up. A growing wait time indicates insufficient Backgrounder capacity.
*   **Job Failures**: Rate of failed jobs. Can indicate resource constraints or configuration issues.
*   **Process Utilization**: Percentage of time Backgrounders are busy vs. idle. Consistent 100% utilization signals a need for more capacity.

**Best Practices for Load Balancing**

**Size Your Deployment Correctly**
*   Assess the volume and frequency of scheduled tasks (extracts, subscriptions).
*   Provision more Backgrounder processes for high-volume, complex extract environments.
*   Start with the default configuration and scale based on monitoring data.

**Isolate Intensive Workloads**
*   Dedicate specific Backgrounder processes to high-priority or resource-heavy tasks using job pools (available in newer Tableau versions).
*   This prevents a large extract refresh from blocking time-sensitive subscription emails.

**Manage Job Scheduling**
*   Stagger scheduled extract refresh times. Avoid scheduling many large extracts at the same hour.
*   Use off-peak hours for intensive maintenance jobs.

**Monitor and Adjust Regularly**
*   Review queue length and job completion times weekly.
*   Add Backgrounder capacity if average wait times consistently exceed service level targets.

**Advanced Topic: Job Pools**
Newer Tableau versions introduce job pools for finer control.

**Pool Concept**
*   Job pools group specific Backgrounder processes.
*   You can assign tasks to a specific pool.

**Use Cases**
*   Create a "Subscriptions" pool to ensure alert and subscription jobs are not delayed by long extract refreshes.
*   Create a "Priority Extracts" pool for business-critical data.

**Limitations**
*   Pools are an advanced feature requiring specific licensing.
*   Misconfiguration can lead to pool starvation or imbalance.

**Conclusion**
Backgrounder load balancing is a core function for performance in Tableau environments. It uses a shared queue model to distribute asynchronous tasks across available processes. Effective management requires correct initial sizing, continuous monitoring of queue metrics, and adjustment based on workload patterns. For on-premises deployments, administrators can scale Backgrounders horizontally across nodes. For Tableau Cloud, capacity is managed by the provider, but customers must design efficient task schedules. Proper load balancing ensures reliable and timely completion of data refreshes, alerts, and subscriptions.
