DevOps Foundations: Version Control and CI/CD with Jenkins OCT 2025 batch 1- Shared screen with speaker view
Nov 2, 2025 06:29 PM Trainer Patel Sir
Time: 04:12:00

https://simplilearn-net.zoom.us/rec/play/6pn-eBYlq_83C5uVhudCX8oQiP16LpfgjL-nU8l_PDdoVo6FcqpP8FqJrL1ULGxZl7hlg7Usl2BArY4.PSU7rOF4-zptuH10?eagerLoadZvaPages=&isReferralProgramEnabled=false&isReferralProgramAvailable=false&accessLevel=meeting&hasValidToken=true&registerToken=Ziy2JIfFsi703svOzqcXd4IBz2hJkOCjwgrc88K8_i0.AG.YQx9lQ121VO34d-dly3ChbSqTGU6pDWARbcZVVkTzgBnHC-t5KyfOvfcADJp5qsfMyQyfRo_eFXOxdoNmwzy4wETG_zL009kYfM7ATKcDeT0jJ7RHeX5c0NjT7Byx3X9Mou7BU06uUp3pyO_E6LUdPkTUb4D3izlwRv84gPAvfzrIw.pPYvoeNspAYU-jjy7IsK_w.Nq1mHMD5vEpWQJjs&canPlayFromShare=true&from=share_recording_detail&startTime=1762088364000&tk=Ziy2JIfFsi703svOzqcXd4IBz2hJkOCjwgrc88K8_i0.AG.YQx9lQ121VO34d-dly3ChbSqTGU6pDWARbcZVVkTzgBnHC-t5KyfOvfcADJp5qsfMyQyfRo_eFXOxdoNmwzy4wETG_zL009kYfM7ATKcDeT0jJ7RHeX5c0NjT7Byx3X9Mou7BU06uUp3pyO_E6LUdPkTUb4D3izlwRv84gPAvfzrIw.pPYvoeNspAYU-jjy7IsK_w.Nq1mHMD5vEpWQJjs&componentName=rec-play&originRequestUrl=https%3A%2F%2Fsimplilearn-net.zoom.us%2Frec%2Fshare%2Fmc0oX50prBunHNyrgB9aHNt1q6SEUjH6QUNGJqBW1a4lUXTWI4myN2vMGCUagtsZ.zywmBn-RSekILuob%3Ftk%3DZiy2JIfFsi703svOzqcXd4IBz2hJkOCjwgrc88K8_i0.AG.YQx9lQ121VO34d-dly3ChbSqTGU6pDWARbcZVVkTzgBnHC-t5KyfOvfcADJp5qsfMyQyfRo_eFXOxdoNmwzy4wETG_zL009kYfM7ATKcDeT0jJ7RHeX5c0NjT7Byx3X9Mou7BU06uUp3pyO_E6LUdPkTUb4D3izlwRv84gPAvfzrIw.pPYvoeNspAYU-jjy7IsK_w.Nq1mHMD5vEpWQJjs%26startTime%3D1762088364000


### 1. Steps to configure a Node using Username and Password:

No Plugin Required:

Jenkins itself provides the core functionality to add and manage nodes (formerly called slaves) without requiring a specific plugin for the basic setup. You can add a permanent agent directly through the Jenkins UI by navigating to Manage Jenkins > Manage Nodes and Clouds > New Node.



Prerequisites:

- Two EC2 instances (Master and Agent) with the same Security group

- Security group inbound rules:

    - Allow All Traffic from 0.0.0.0/0
    
    - Allow TCP traffic on port 8080 for Jenkins
    
    - Allow SSH traffic (port 22)

Master Node Configuration:

1. Install Java and Jenkins on the Master node

2. Become a root user: sudo -s

3. Access Jenkins UI: http://<Master-Node-Public-IP>:8080

Agent Node Configuration:

1. Update SSH configuration: sudo vi /etc/ssh/sshd_config
    
    - Set PermitRootLogin yes (Line 42)
    
    - Uncomment PasswordAuthentication yes (Line 66)

2. Update cloud-init configuration: sudo vi /etc/ssh/sshd_config.d/60-cloudimg-settings.conf

    - Set PasswordAuthentication yes

3. Set a password for the ubuntu user: sudo passwd ubuntu

4. Restart SSH service: sudo service ssh restart

Jenkins UI Configuration:

1. Go to Manage Jenkins > Manage Nodes and Clouds > New Node

2. Create a new node:

    - Name: Agent
    
    - Description: Agent node
    
    - Number of executors: 1
    
    - Remote root directory: /home/ubuntu
    
    - Labels: Agent-Node
    
    - Usage: Only build jobs with label expressions matching this node
    
    - Launch method: Launch agents via SSH
    
    - Host:  < Agent-Node-Public-IP >
    
    - Credentials:
    
        - Click Add > Jenkins
        
        - Select Username with password
        
        - Enter ubuntu as username and the password set earlier

    - Host Key Verification Strategy: Non verifying Verification Strategy

4. Click Save and Apply

Verification:

1. Go to Manage Jenkins > Manage Nodes and Clouds

2. Verify that the Agent node is online and connected

### 2. Steps to configure a Node using Username and Private key :

