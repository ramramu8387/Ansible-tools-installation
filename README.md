# Ansible-tools-installation
Tools installation in multiple hosts using Ansible

Step-1 :- Launch 4 instances for MASTER, Slave-1, Slave-2 and Slave-3 with below features.

1.MASTER AMI = Amazon Linux Kernel 6.18, Instance type = c7i-flex.large, EBS = 15 GB, Security Groups=SSH,8080

2.Slave-1 AMI = Amazon Linux Kernel 6.18, Instance type = c7i-flex.large, EBS = 15 GB, Security Groups=SSH,8080

3.Slave-2 AMI = Amazon Linux Kernel 6.18, Instance type = c7i-flex.large, EBS = 15 GB, Security Groups=SSH,8080

4.Slave-3 AMI = Amazon Linux Kernel 6.18, Instance type = c7i-flex.large, EBS = 15 GB, Security Groups=SSH,8080

<img width="1112" height="350" alt="image" src="https://github.com/user-attachments/assets/331264fc-3916-44a2-8242-c4face4b97e2" />

Step-2 :- Set Hostname to all servers as like below

1. MASTER

<img width="566" height="339" alt="image" src="https://github.com/user-attachments/assets/1e353a02-a8c5-496a-8e18-6b9939675125" />

2. Slave-1

<img width="556" height="390" alt="image" src="https://github.com/user-attachments/assets/43b9643c-c421-4f4a-9a7c-c502de8472bc" />

3. Slave-2

<img width="545" height="330" alt="image" src="https://github.com/user-attachments/assets/416f9b49-8320-4e69-9c52-97c70af3fe37" />

4. Slave-3

<img width="544" height="347" alt="image" src="https://github.com/user-attachments/assets/8fa62532-c967-401a-92d5-399b572ef46a" />

Step-3 :- Install Ansible & Python-pip on MASTER server.

Commands :-

yum install ansible -y
yum install python-pip -y

<img width="1349" height="721" alt="image" src="https://github.com/user-attachments/assets/48bfa67c-0c0e-480a-9e4f-34df1bc98d78" />

Step-4 :- Set root password to all master & slave servers.

passwd root

<img width="480" height="103" alt="image" src="https://github.com/user-attachments/assets/dd20c9f3-7169-465f-b125-a990fd33bcb1" />

Step-5 :- Now we have to say yes to Password Authentication & Restart SSHD on All Master & Slave server.

vi /etc/ssh/sshd_config

In the line 40 remove # and type yes & in the line 65 remove no and type yes at the Password Authentication.

<img width="271" height="21" alt="image" src="https://github.com/user-attachments/assets/bc69ea9a-58d0-42b5-b811-dbb112f653a9" />

systemctl restart sshd

Step-6 :- Generate a SSH KEY in Ansible user on MASTER server using below command.

ssh-keygen

<img width="596" height="354" alt="image" src="https://github.com/user-attachments/assets/683d1b5e-1f30-4098-b35c-a7eaeacb1555" />

Step-7 :- Copy the public key to all slave servers from master using below command.

ssh-copy-id root@slave-private-ip

Step-8 :-  Add inventories to the below path on MASTER server.

vi /etc/ansible/hosts

<img width="137" height="143" alt="image" src="https://github.com/user-attachments/assets/44121be4-f837-4f99-b7e1-5a7abbebfda8" />

Step-9 :- Check the connection with all slave servers using below command.

ansible all -m ping

<img width="1348" height="478" alt="image" src="https://github.com/user-attachments/assets/c0d50c59-3956-4935-958c-069808c27327" />

Step-10 :- Write a Playbook to install git on dev group.


