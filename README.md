# <a name="Top">Dynatrace Managed Installation</a>
This repository will contain a guide on how to deploy a Dynatrace Managed Cluster. After deploying the cluster we will install: a cluster ActiveGate, an environment ActiveGate, the OneAgent, and EasyTravel. The below list can be used for navigation.  
1. [Getting Started](#GettingStarted)  
1. [Installing a Managed Cluster](#ManagedCluster)
    1. [Installation](#installation)
    1. [Connecting to the Managed Cluster](#ConnectCluster)
    1. [Overview of the Cluster Management Console](#CMC)
1. [Installing a Cluster ActiveGate](#ClusterActiveGate)
1. [Installing an Environment ActiveGate](#EnvironmentActiveGate)
1. [Installing OneAgent](#OneAgent)
1. [**Optional** - Installing EasyTravel](#EasyTravel)  
  [Glossary](#Glossary)
# <a name="GettingStarted">Getting Started</a> <sub><sup>[Back to Top](#Top)</sup></sub>
## Navigation:  
The sections can be jumped to by clicking the section name above. There will be a glossary of terms at the end of the file. If more help is needed or you desire additional clarification, an effective too to use can be found [here](https://www.dynatrace.com/support/help/).
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
- ## <a name="Installation">Installation</a> [Back to Top](#Top)</sup></sub>
An email will be sent to you with your installation link. Each of these links is unique and is tied to your Dynatrace account.
Inside your linux terminal execute the commands in the email(pictured below for reference):
![Managed Email](/images/email_example.png)  
In the picture above we can see there are links to the documentation for requirements and the commands to be executed. Each of these commands is unique to your managed environment.
1. Run the first command:  
![Download Installer](/images/installer.png)
1. Verify the installation. Expected output:
![Verification Image](/images/verification.png)
1. After verifying installation, as **ROOT** run the installer at /bin/sh dynatrace-managed.sh, with the flag --license stringHere. stringHere is where you will replace with your license ky from the email.  
![Install Command](/images/install_command.png)  
1. Read and Accept the Terms of Service.  
![Terms](/images/terms.png)  
1. The following prompts will be to modify your installation, I am leaving these as the default so I will just press ENTER when prompted.
1. Wait for the installer to finish.  
![Inatalling](/images/install.png)  
Expected Ouptut:  
![Installation Complete](/images/installed.png)  
The output of the installer shows where Dynatrace will store information. These locations are related to the parameters prompted by the installer (which I left as default).  
**Note:** The Dynatrace Managed cluster is a greedy application and wil use all space available, this necessitates having a dedicated machine to run the cluster. See the link for hardware requirements above for a thorough breakdown.  
Our Dynatrace Managed cluster is now running. The IP provided by the installer will be used for later sections. Typically your cluster IP would be reachable, however as I am using an EC2 instance I will be using the public IP of that instance to connect to my cluster.  
- ## <a name="ConnectCluster">Connecting to Managed Cluster</a> [Back to Top](#Top)</sup></sub>
Using the provided IP ![IP](/images/address.png), connect to your Managed Cluster. On, initial visit you will be prompted to enter some basic information. As seen below:  
![Initial Visit](/images/signin.png)  
Fill out the application to get started!  
The landing page should look something similar to:
![Cluster Management Console](/images/cmc.png)  
# <a name="ClusterActiveGate">Installing a Cluster ActiveGate</a> <sub><sup>[Back to Top](#Top)</sup></sub>  
## Configure ActiveGate to communicate with  Cluster.    
1. Select Cluster Node segment of your Home environment.  
![Cluster Node](/images/clusternode.png)  
1. Select the Cluster Node we created in the above steps.  
![My Cluster Node](/images/picknode.png)  
The values that we are goin to change can be seen here:  
![ip](/images/valuestochange.png)  
1. Select "Configure"  
1. Change Node End Points. These values are the Ip adresses that you managed cluster will be able to communicate to, the ports that are important are 443, and 9999. The network must allow for traffic through these ports.We change these values to be the IP of the Cluster.  
![Node End Point](/images/endpoint.png)  
1. Select Update Configuration.  
## Install Cluster ActiveGate
1. Navigate to the "Home" screen. By selecting Home from the hamburger menu.  
![Home](/images/home.png)  
1. For this section we will install a Cluster ActiveGate, the easest way to do this is: from the home screen select the ... in the top right-hand corner and select "Add new Cluster ActiveGate":  
![New Cluster ActiveGate](/images/addnewcag.png)   
1. Choose Operating System (Linux in this case.)  
![Operating System](/images/1dlcag.png)  
1. Copy the commands into your Linux terminal. Add '''--no-check-certificate''' to the wget command.  
![Commands](/images/2downloadcag.png)   
1. Run the wget command. Be sure to append '''--no-check-certificate'''. Expected output:   
![Install Command](/images/3install.png)  
1. Wait for installation to finish.  
![Installation Finished](/images/activegatecli.png)  
**Note:** If you see unable to connect, double check the ActiveGate Ip in the Cluster Node.  
1. asdasdasd
# <a name="EnvironmentActiveGate">Installing an Environment ActiveGate</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="OneAgent">Installing OneAgent</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="EasyTravel">**Optional** -Installing EasyTravel</a> <sub><sup>[Back to Top](#Top)</sup></sub>
# <a name="Glossary">Glossary</a> <sub><sup>[Back to Top](#Top)</sup></sub>
