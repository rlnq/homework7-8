# This ansible project helps you harden user passwords (apply to "root") by rejecting passwords that contain the username on your remote hosts.

## Prerequisites:

Install Ansible on the main server: You will need to have Ansible installed on the main server in order to manage the nodes. You can install Ansible using the package manager for your operating system.

> `sudo apt update -y`

> `sudo apt install python3-pip -y`

> `sudo python3 -m pip install ansible`

Use 'git clone' to clone this repository using Git

> `git clone https://github.com/rlnq/homework7-8.git`

Configure the Ansible inventory: change specify the IP addresses or hostnames of the nodes in 'hosts' you want to connect to.

Configure SSH access: Ansible uses SSH to connect to the nodes. You will need to configure SSH access on the main server and the nodes. 
On the main server, you will need to generate an SSH key ( `ssh-keygen` ) and copy the public key ( ~/.ssh/id_rsa.pub ) to the nodes. 
On the nodes, you will need to add the public key to the authorized_keys file ( ~/.ssh/authorized_keys ).

