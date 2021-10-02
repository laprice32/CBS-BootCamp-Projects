 ## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ jollie_wiles

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ Load Balancers protect servers from Denial of Service attacks. Load Balancers distribute the data to the server. Jumpbox protects the virtual machines from the public.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.
- _TODO: What does Filebeat watch for? Filebeat watches and monitors the log files or locations that users specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- _TODO: What does Metricbeat record? takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web-1    | Web Server| 10.0.0.7   | Linux            |
| Web-2    | Web Server| 10.0.0.8   | Linux            |
| Web-3    | Web Server| 10.0.0.9   | Linux        

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _SSH laprice32@13.92.25.25

Machines within the network can only be accessed by the Jump Box Machine.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Private IP Address from Jump Box is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |  Yes                | 154.6.21.59          |
|  Web-1   |  No                 | 10.0.0.4             |
|  Web-2   |  No                 | 10.0.0.4             |
|  Web-3   |  No                 | 10.0.0.4             |
|  ELK     |  No                 | 10.1.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

Install Docker
Install python3-pip
Install Docker python module
Set the vm.max_map_count to 262144
Download and launch a docker elk container
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.4 10.0.0.7 10.0.0.8 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat
  Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat monitors the log files or locations that you specify so you can see the changes in the log files. Metricbeat records the metrics and statistics from the operating system and running services.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible file to /etc/ansible.
- Update the install-elk.yml file to include the machine you want to use the playbooks on. by changing the hostnames on the 3rd line.
- Run the playbook, and navigate to http://{your.VM.IP}:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? edit the /etc/ansible/host file to add webserver/elkserver ip addresses
- _Which URL do you navigate to in order to check that the ELK server is running? www.myip:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._