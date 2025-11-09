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


### Jenkins Control Node and Slave Node

##### In Jenkins, a Slave node is a machine that is connected to the Master node (the machine where Jenkins is installed) and is used to execute build jobs.

To define a Slave node in Jenkins, you'll need to create a new node in the Jenkins web interface and configure it to connect to the Master node. Here are the general steps:

1. Go to the Jenkins web interface and click on "Manage Jenkins" > "Manage Nodes and Clouds".
2. Click on "New Node" and enter a name for the Slave node.
3. Select "Permanent Agent" as the node type.
4. Configure the node settings, such as the remote root directory, labels, and launch method (e.g., SSH, JNLP, etc.).
5. Save the node configuration.

The Slave node will then connect to the Master node and register itself as a available node for executing build jobs.

In the context of Jenkins, the terms "Master" and "Slave" are used to describe the relationship between the Jenkins server (Master) and the machines that execute build jobs (Slaves). However, it's worth noting that these terms are being replaced with more modern and inclusive language, such as "Controller" and "Agent", in newer versions of Jenkins.

In your case, if you have two EC2 instances, one with Jenkins installed (the Master) and the other one that is the Slave, then you can define the Slave node in the Jenkins web interface and configure it to connect to the Master node using the steps I outlined above.


Q. A slave node is where  a Jenkins job is runned, so can i say that the slave node also have Jenkins installed in it thats why it is able to run the same Jenkins job  that can be ranned on the master ?

Sol: 

No, that's not entirely accurate. A Slave node (or Agent node) in Jenkins doesn't necessarily have Jenkins installed on it. Instead, it has a Jenkins Agent (also known as a Slave Agent) running on it, which communicates with the Master node.

The Jenkins Agent is a lightweight process that runs on the Slave node and receives instructions from the Master node to execute build jobs. The Agent is responsible for executing the job, collecting the results, and sending them back to the Master node.

The Slave node doesn't need to have the full Jenkins installation, as it relies on the Master node to provide the job configuration, scripts, and other necessary resources.

Think of it like this:

- Master node: The controller, responsible for managing jobs, providing configuration, and coordinating the build process.
- Slave node: A worker machine that executes the build jobs, using the Jenkins Agent to communicate with the Master node.

So, while the Slave node doesn't have a full Jenkins installation, it does have the necessary components to run build jobs, thanks to the Jenkins Agent.


Q. Is it that the Jenkins agent is responsible to build a job ?

Sol: 

The Jenkins Agent is responsible for executing a job, but I wouldn't say it's solely responsible for "building" a job.

A more accurate statement would be:

"The Jenkins Agent is responsible for running a job on behalf of the Master node, executing the tasks and commands defined in the job configuration."

The Jenkins Agent doesn't actually "build" the job itself. Instead, it:

1. Receives the job configuration and instructions from the Master node.
2. Executes the tasks and commands defined in the job configuration.
3. Collects the output and results of the job execution.
4. Sends the results back to the Master node.

The "building" of the job is actually done by the tools and scripts defined in the job configuration, such as compilers, build tools, and scripts. The Jenkins Agent simply provides the environment and resources needed to execute those tasks.

Think of job execution as a relay, where the Master node sends the job to the Agent, and the Agent executes the job and reports back to the Master.

Q. So is it that a Jenkins agent is also on the master node that does the same thing ?

Sol: 

Yes, that's correct! The Master node in Jenkins also runs a Jenkins Agent, which is responsible for executing jobs on the Master node itself.

In other words, the Master node is both a controller (managing jobs, configuration, and coordination) and an Agent (executing jobs).

This means that the Master node can execute jobs locally, using its own Agent, in addition to delegating jobs to other Agent nodes.

So, to summarize:

- Master node: Runs a Jenkins Agent, and is responsible for managing jobs, configuration, and coordination.
- Slave node (or Agent node): Runs a Jenkins Agent, and is responsible for executing jobs delegated by the Master node.

Thanks for pointing out the clarification!

Q: **So it is the Jenkins agent both on master and slave that executes a job and not the node ?**

Sol:

The Jenkins Agent, whether running on the Master node or a Slave node, is the component responsible for executing a job. The node (Master or Slave) provides the environment and resources for the Agent to run, but it's the Agent itself that actually executes the job.

Think of it like this:

- Node (Master or Slave): Provides the environment, resources, and connectivity.
- Jenkins Agent: Executes the job, runs tasks and commands, and collects results.

So, to be precise, it's the Jenkins Agent that executes a job, not the node itself. The node is more like a host for the Agent, providing the necessary infrastructure for the Agent to do its work.


**Q: Could you please explain why you added the public key of the slave node to the authorized keys file ?**

Sol: 
When setting up a Jenkins Slave node, you typically need to establish a secure connection between the Master node and the Slave node. One way to do this is by using SSH (Secure Shell) authentication.

To enable SSH authentication, you'll need to add the public key of the Slave node to the authorized_keys file on the Slave node. Here's why:

1. Authentication: The Master node needs to authenticate itself to the Slave node to establish a secure connection. By adding the public key of the Slave node to the authorized_keys file, you're allowing the Master node to authenticate itself using its private key.
2. Authorization: The Slave node checks the authorized_keys file to verify that the incoming connection (from the Master node) is authorized to access the node. If the public key is present in the file, the Slave node grants access to the Master node.
3. Secure Connection: With the public key in place, the Master node can establish a secure SSH connection to the Slave node, and the Jenkins Agent on the Slave node can communicate with the Master node securely.

By adding the public key of the Slave node to the authorized_keys file, you're essentially allowing the Master node to connect to the Slave node using SSH, which enables the Jenkins Agent to receive job execution instructions from the Master node.

Here's a high-level overview of the process:

1. Generate a public-private key pair on the Master node (if you haven't already).
2. Copy the public key to the Slave node and add it to the authorized_keys file.
3. Configure the Jenkins Master node to use the private key to connect to the Slave node.
4. When the Master node needs to execute a job on the Slave node, it uses the private key to authenticate and establish a secure SSH connection.
5. The Jenkins Agent on the Slave node receives job execution instructions from the Master node and executes the job.

This setup enables secure communication between the Master node and the Slave node, allowing you to execute jobs on the Slave node remotely.


Q: Explain the above with a simple example or a real worls example and more elaborately ?

Sol:

Let's break it down with a simple example:

Example:

Suppose you have two computers:

- Master Node (Computer A): This is your Jenkins server, running on IP address 192.168.1.100.
- Slave Node (Computer B): This is your build machine, running on IP address 192.168.1.200.

You want to set up Computer B as a Jenkins Slave node, so it can execute build jobs sent by Computer A (the Master node).

Step 1: Generate SSH keys on Computer A (Master Node)

You generate a public-private key pair on Computer A using a tool like ssh-keygen. This creates two files:

- id_rsa (private key)
- id_rsa.pub (public key)

Step 2: Copy public key to Computer B (Slave Node)

You copy the contents of id_rsa.pub (the public key) to Computer B and add it to the authorized_keys file. This file is usually located in the ~/.ssh directory.

What's happening here?

When you add the public key to authorized_keys, you're essentially saying: "Hey, Computer B, allow Computer A to connect to you using this public key."

Step 3: Configure Jenkins on Computer A

In the Jenkins web interface, you configure the Slave node (Computer B) and specify the SSH connection details:

- Host: 192.168.1.200 (IP address of Computer B)
- Credentials: Use the private key (id_rsa) generated in Step 1

How it works:

1. When Jenkins on Computer A needs to execute a job on Computer B, it uses the private key (id_rsa) to establish an SSH connection to Computer B.
2. Computer B receives the connection request and checks the authorized_keys file. Since the public key is present, it verifies that the connection is authorized.
3. Computer B grants access to Computer A, and the SSH connection is established.
4. Jenkins on Computer A sends the job execution instructions to Computer B.
5. The Jenkins Agent on Computer B receives the instructions and executes the job.

Real-world analogy:

Think of it like a secure mailbox:

- Computer A (Master Node) is like a person who wants to send a confidential letter to Computer B (Slave Node).
- The public key is like a lock that Computer A uses to secure the letter.
- The private key is like the key that only Computer A has, which unlocks the lock.
- The authorized_keys file is like a list of trusted locks that Computer B has authorized.
- When Computer A sends the letter (job execution instructions), Computer B checks the lock (public key) and verifies that it's from a trusted source (Computer A).
- If everything checks out, Computer B unlocks the letter (executes the job) and sends the results back to Computer A.

This process ensures a secure connection between the Master node and Slave node, allowing you to execute jobs remotely.


- Here's an elaborated explanation:

Why was the public key of the Slave node added to the authorized_keys file?

When setting up a Jenkins Slave node, it's essential to establish a secure connection between the Master node and the Slave node. One way to achieve this is by using SSH (Secure Shell) authentication, which relies on public-key cryptography.

In this context, the public key of the Slave node is added to the authorized_keys file on the Slave node itself. This might seem counterintuitive at first, as you might expect the Master's public key to be added instead. However, the reasoning behind this is as follows:

1. The Slave node is the server: In this SSH connection, the Slave node acts as the server, and the Master node acts as the client. The Slave node needs to verify the identity of the Master node before allowing it to connect and execute jobs.
2. Authentication and authorization: By adding the Slave node's public key to the authorized_keys file, you're essentially saying: "Allow the Master node to connect to this Slave node using the corresponding private key."
3. Key pair mismatch: If you were to add the Master's public key to the authorized_keys file, it would imply that the Slave node is trying to connect to the Master node, which is not the case. The Master node initiates the connection, so it needs to present the Slave node's public key to authenticate itself.

To clarify, here's what should happen:

- The Master node generates a public-private key pair.
- The Slave node's public key is added to the authorized_keys file on the Slave node.
- The Master node's private key is used to connect to the Slave node.

However, in the context of Jenkins, it's more common to use the Master's public key and add it to the Slave node's authorized_keys file. This allows the Master node to authenticate itself to the Slave node.

To summarize:

- The public key of the Slave node is not typically added to the authorized_keys file.
- Instead, the Master's public key is added to the Slave node's authorized_keys file, allowing the Master node to connect and execute jobs on the Slave node.

Here's an updated example:

- Generate a public-private key pair on the Master node.
- Copy the Master's public key to the Slave node and add it to the authorized_keys file.
- Configure Jenkins to use the private key to connect to the Slave node.

By doing so, you establish a secure connection between the Master node and the Slave node, enabling the Master node to execute jobs on the Slave node securely.

- Yes, to establish a secure SSH connection between two machines, you typically need to follow these steps:

1. Generate a public-private key pair on one machine (the client).
2. Copy the public key to the other machine (the server) and add it to the authorized_keys file.
3. Use the private key to connect to the server from the client.

Let's elaborate with an example:

Example:

Suppose we have two machines:

- Machine A (Client): IP address 192.168.1.100
- Machine B (Server): IP address 192.168.1.200

We want to establish an SSH connection from Machine A to Machine B.

Step 1: Generate public-private key pair on Machine A (Client)

Run the command ssh-keygen on Machine A to generate a public-private key pair:

bash
ssh-keygen -t rsa

This generates two files:

- id_rsa (private key)
- id_rsa.pub (public key)

Step 2: Copy public key to Machine B (Server)

Copy the contents of id_rsa.pub (the public key) to Machine B:

bash
scp id_rsa.pub user@192.168.1.200:~/

Step 3: Add public key to authorized_keys file on Machine B (Server)

On Machine B, add the public key to the authorized_keys file:

bash
cat id_rsa.pub >> ~/.ssh/authorized_keys

Step 4: Connect to Machine B (Server) from Machine A (Client)

Use the private key to connect to Machine B from Machine A:

bash
ssh -i id_rsa user@192.168.1.200

If everything is set up correctly, you should be able to establish an SSH connection from Machine A to Machine B.

What's happening behind the scenes:

1. Machine A (Client) initiates an SSH connection to Machine B (Server).
2. Machine B (Server) requests authentication from Machine A (Client).
3. Machine A (Client) sends the public key (id_rsa.pub) to Machine B (Server).
4. Machine B (Server) checks the authorized_keys file and verifies that the public key is authorized.
5. Machine B (Server) generates a random session key and encrypts it with the public key.
6. Machine A (Client) decrypts the session key using the private key (id_rsa).
7. Machine A (Client) and Machine B (Server) establish an encrypted SSH connection.

By following these steps, you've established a secure SSH connection between Machine A and Machine B, allowing you to securely access and manage Machine B from Machine A.

#### Let's dive into the .ssh directory and its files.

*What is the .ssh directory?*

The .ssh directory is a hidden directory located in a user's home directory (e.g., /root/.ssh or /home/user/.ssh). It's used to store SSH-related files, including private keys, public keys, and configuration files.

*Files in the .ssh directory:*

1. *authorized_keys*: This file contains a list of public keys that are authorized to connect to the server via SSH. When a client tries to connect, the server checks this file to verify the client's public key.
2. *id_rsa*: This is a private key file generated by the ssh-keygen command. It's used for authentication and encryption.
3. *id_rsa.pub*: This is the public key file corresponding to the private key (id_rsa). It's shared with servers to establish trust.

*What happens when you run ssh-keygen?*

When you run ssh-keygen, it generates a public-private key pair:

1. The private key (id_rsa) is stored in the .ssh directory.
2. The public key (id_rsa.pub) is also stored in the .ssh directory.

Why were the key files not there initially?

The key files (id_rsa and id_rsa.pub) are not created automatically. They are generated when you run the ssh-keygen command. If you haven't run ssh-keygen before, the files won't exist.

Use cases for the files:

1. *authorized_keys*: Add public keys of clients that should be allowed to connect to the server via SSH.
2. *id_rsa*: Use this private key to connect to servers that have your public key (id_rsa.pub) in their authorized_keys file.
3. *id_rsa.pub*: Share this public key with servers to establish trust and allow connections from your client.

Example scenario:

1. You generate a key pair on your local machine (id_rsa and id_rsa.pub).
2. You copy the public key (id_rsa.pub) to a remote server and add it to the authorized_keys file.
3. You use the private key (id_rsa) to connect to the remote server via SSH.

In your case, since you've generated a key pair, you can now use the private key (id_rsa) to connect to other servers that have your public key (id_rsa.pub) in their authorized_keys file.

Here's a summary:

- authorized_keys: List of trusted public keys.
- id_rsa: Private key for authentication and encryption.
- id_rsa.pub: Public key shared with servers to establish trust.

Feel free to ask if you have more questions!


