### Nodes/Agents/Slaves

https://github.com/dpakGit/100_Days_of_DevOps/tree/main/100_Day_Tasks/Day_75%3A_Jenkins_Slave_Nodes

https://www.youtube.com/watch?v=ANMAOmr6yN0

In Jenkins, the terms "agent" and "slave" (or "node") are often used interchangeably, but there is a subtle distinction.

**Slave Node**: In older versions of Jenkins (before 2.0), a slave node referred to a machine that was connected to a master node and executed tasks assigned to it. The master node would distribute tasks to the slave nodes, which would then execute the tasks.

**Agent**: In modern Jenkins (2.0 and later), the term "agent" is used instead of "slave". An agent is a machine that connects to the Jenkins master and executes tasks. Agents can be:

1. Permanent agents: These are machines that are always connected to the Jenkins master and are available to execute tasks.

2. Cloud agents: These are machines that are dynamically provisioned and deprovisioned by Jenkins as needed.

3. Docker agents: These are containers that run on a Docker host and execute tasks.

In essence, an agent is a more modern and flexible concept than a slave node. While the terms are often used interchangeably, "agent" is the preferred term in modern Jenkins documentation and configurations.

A Jenkins agent and a slave node are essentially the same thing, but "agent" is the more contemporary and accurate term.

### Steps to configure a Node

No Plugin Required:

Jenkins itself provides the core functionality to add and manage nodes (formerly called slaves) without requiring a specific plugin for the basic setup. You can add a permanent agent directly through the Jenkins UI by navigating to Manage Jenkins > Manage Nodes and Clouds > New Node.
