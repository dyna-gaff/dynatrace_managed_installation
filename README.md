# <a name="Top">Dynatrace Managed Installation</a>
This repository will contain a guide on how to deploy a Dynatrace Managed Cluster. After deploying the cluster we will install: a cluster ActiveGate, an environment ActiveGate, the OneAgent, and EasyTravel. The below list can be used for navigation.  
1. [Getting Started](#GettingStarted)  
1. [Installing a Managed Cluster](#ManagedCluster)
1. [Installing a Cluster ActiveGate](#ClusterActiveGate)
1. [Installing an Environment ActiveGate](#EnvironmentActiveGate)
1. [Installing OneAgent](#OneAgent)
1. [**Optional** - Installing EasyTravel](#EasyTravel)  
  [Glossary](#Glossary)
# <a name="GettingStarted">Getting Started</a> <sub><sup>[Back to Top](#Top)</sup></sub>
## Requirements:
- ### Dynatrace Managed:
The requirements for Dynatrace Managed will vary depending on the size of the cluster:

| Node Type | Max Hosts Monitored(per node) | Peak User Actions/min(per node) | Min Node Specifications | Disk IOPS(pernode) | Transaction Storage (10 days code visibility) | Long-term Metrics Store (per node) | Elasticsearch(per node)(35 days retention) |
|--------|--------|--------|--------|--------|--------|--------|--------|
|Micro|50|1000|4 vCPUs, 32GB RAM|30|50GB|100GB|50GB|
|Small|300|10000|8 vCPUs, 64GB RAM|100|300GB|500GB|500GB|
|Medium|600|25000|16 vCPUs, 128GB RAM|300|600GB|1TB|1.5TB|
|Large|1250|50000|32 vCPUs, 256GB RAM|750|1TB|2TB|1.5TB|
|XLarge|2500|100000|64 vCPUs, 512GB RAM|1500|2TB|4TB|3TB|

<sub><sup>For a more detailed breakdown, pleave visit the [Dynatrace Managed documentation](https://www.dynatrace.com/support/help/setup-and-configuration/dynatrace-managed/installation/dynatrace-managed-hardware-and-system-requirements/).</sup></sub>  
- ### ActiveGates (**Each**)
  - 2 GB free disk space
  - 2 GB RAM(4 GB Recommended)
  - 1 dual core processor
  - Windows or Linux Operating System
- ### Dynatrace Managed One-Agent
OneAgent self-monitoring for Dynatrace Managed requires 4.8 GB of disk space on Linux. 
The ability to use root privileges for installation. 
- ### This lab:
For the followig demonstration three **dedicated** machines will be used for hosting components, with a fourth machine having the OneAgent installed. I will be using an Amazon EC2 instance with Linux installed, two virtual machines with Ubuntu(64-bit) Operating Systems installed. The fourth machine, running the OneAgent and EasyTravel, will be   
## Prerequisite:

# <a name="ManagedCluster">Installing a Managed Cluster</a> <sub><sup>[Back to Top](#Top)</sup></sub>
An email will be sent to you with your installation link. Each of these links is unique and is tied to your Dynatrace account.
Inside your linux terminal execute the commands in the email(pictured below for reference):
![Managed Email](/images/email_example.png)
In the picture above we can see there are links to the documentation for requirements and the command to be executed.
1. Run the first command:  
![Download Installer](/images/installer.png)
1. Verify the installation. Expected output:
![Verification Image](/images/verification.png)
# <a name="ClusterActiveGate">Installing a Cluster ActiveGate</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="EnvironmentActiveGate">Installing an Environment ActiveGate</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="OneAgent">Installing OneAgent</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="EasyTravel">**Optional** -Installing EasyTravel</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="Glossary">Glossary</a> <sub><sup>[Back to Top](#Top)</sup></sub>
