# Cybersec_Files
Files created during my cybersecurity bootcamp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Images/Screenshot%20(341).png) 


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, this document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting traffic to the network.
- Load balancers protect servers from being flooded with network traffic that could be a result of a DoS attack. The advantage of a jump box is the flexibility and    versatility. It is cost efficient and provides a ton of options.  
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to files and system configuraitons.
- Filebeat watches for changes within files.
- Metricbeat records systems logs (i.e. opening and closing docker container).

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.1.0.10  | Linux            |
| Web-1    | Web Server| 10.1.0.8   | Linux            |
| Web-2    | Web Server| 10.1.0.9   | Linux            |
| ELK Sever| Logstash  | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box  machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 10.1.0.8
- 10.1.0.9
- 10.0.0.4

Machines within the network can only be accessed by SSH.
- Only the jump box machine (10.1.0.10) has access to the ELK VM via SSH.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses      |
|----------|---------------------|---------------------------|
| Jump Box | Yes                 | 10.1.0.8 10.1.0.9 10.0.0.4|
| Web-1    | No                  | 10.1.0.10                 |
| Web-2    | No                  | 10.1.0.10                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is faster and more efficient than configuring each individual machine one at a time. 

The playbook implements the following tasks:
- Install Docker.io, pip3, and Docker python module
- Increase virtual memory
- Use Docker container module to download and launch docker ELK container
- Download the image
- List ports to be operating in

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](Images/Screenshot%20(359).png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.1.0.8
- Web-2: 10.1.0.9

We have installed the following Beats on these machines:
- Filebeats
  - Web-1
  - Web-2
  - DVWA container

These Beats allow us to collect the following information from each machine:
- The Filebeat collects log data on file system information.
