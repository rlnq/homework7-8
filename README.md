# This ansible project helps you harden user passwords (applies to "root") by rejecting passwords that contain the username on your remote hosts.

For this project we need at least 2 servers: the main ansible server and the node.

Now if we run `passwd root` on the nodes server and enter a password like "root1234" we will see:

<img width="538" alt="Screenshot 2023-01-14 at 15 03 42" src="https://user-images.githubusercontent.com/117667360/212472927-da85fd2f-b259-43c0-ab66-ad8eeef902a9.png">

To fix this, we need to use the libpam-pwquality and cracklib-runtime packages.

`libpam-pwquality` and `cracklib-runtime` are packages that provide password strength-checking functions for PAM (Pluggable Authentication Modules). 
They ensure that passwords meet certain complexity requirements and are not based on commonly used words or patterns.

## Prerequisites:

Install Ansible on the main server: You will need to have Ansible installed on the main server in order to manage the nodes. You can install Ansible using the package manager for your operating system.

```
sudo apt update -y

sudo apt install python3-pip -y

sudo python3 -m pip install ansible
```

## Steps:

Use 'git clone' to clone this repository using Git

> `git clone https://github.com/rlnq/homework7-8.git`

Configure the Ansible inventory: change specify the IP addresses or hostnames of the nodes in 'hosts' you want to connect to.

Configure SSH access: Ansible uses SSH to connect to the nodes. You will need to configure SSH access on the main server and the nodes. 
On the main server, you will need to generate an SSH key ( `ssh-keygen` ) and copy the public key ( ~/.ssh/id_rsa.pub ) to the nodes. 
On the nodes, you will need to add the public key to the authorized_keys file ( ~/.ssh/authorized_keys ).


Then run our ansible project using the command on the ansible server ansible `ansible-playbook -i hosts side.yml `

<img width="1242" alt="Screenshot 2023-01-14 at 15 10 48" src="https://user-images.githubusercontent.com/117667360/212473192-dd77e429-c2ed-483e-8255-0226b147d349.png">

On the node server, we again try to enter passwords like "123456789", "root123" or "ROOT12345" using "passwd root" for the root user and see:

<img width="1221" alt="Screenshot 2023-01-14 at 15 33 08" src="https://user-images.githubusercontent.com/117667360/212474372-015d07d8-8749-4646-b874-6c907a9bea68.png">

We will do the same for the ubuntu user, using passwords such as "123456789", "ubuntu123", "UBUNTU12345"

<img width="1242" alt="Screenshot 2023-01-14 at 15 29 49" src="https://user-images.githubusercontent.com/117667360/212474238-5c61e1da-a9b3-4dfb-93fe-5ec3f23c9b31.png">


