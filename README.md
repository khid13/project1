## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - 

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _logs_and system traffic.
-  What does Filebeat watch for?_
        Filebeat watches for log files and collects log events.
-  What does Metricbeat record?_
        metric and statistical data from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | Backend  | 10.0.0.8   | Linux            |
| Web2     | Backend  | 10.0.0.9   | Linux            |
| Elk      | Backend  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 10.0.0.4: Add whitelisted IP addresses_

Machines within the network can only be accessed by ssh.
- Jump box 10.0.0.4: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
|  Web1    | No                  |  10.0.0.4            |
|  Web2    | No                  |  10.0.0.4            |
|  Elk     | No                  |  10.0.0.4            |                     
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Save time: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker engine
  download and launch elk docker container
  publish ports elk stack runs on
  start docker service
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- : List the IP addresses of the machines you are monitoring_
   10.0.0.8
   10.0.0.9
We have installed the following Beats on these machines:
- : Specify which Beats you successfully installed_
   Filebeat
   Metricbeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
    Metricbeat makes it easy to collect specific information about the machines in the network. Filebeat enables analysts to monitor files for suspicious changes
    Metricbeat collects machine metrics, such as uptime.A metric is simply a measurement about an aspect of a system that tells analysts how "healthy" it is.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml and metricbeat-config.yml file to /etc/ansible/roles/files/.
- Update the configuration file to include...private ip of elk
- Run the playbook, and navigate to elk server_ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:
- _Which file is the playbook? Where do you copy it?
    filebeat-playbook.yml metricbeat-playbook.yml, /etc/ansible/files
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
filebeat-config.yml, metricbeat-config.yml, edit in beat configuration file templates
- _Which URL do you navigate to in order to check that the ELK server is running?
    http://20.227.163.138:5601/app/kibana
