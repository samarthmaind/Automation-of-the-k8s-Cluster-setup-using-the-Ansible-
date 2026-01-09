# Ansible Environment Installation.

Ansible Control Node

Linux system (Ubuntu preferred)

Installed:

sudo apt update

sudo apt install -y ansible sshpass

Check:

ansible --version

SSH Setup (VERY IMPORTANT)

From control node:

ssh-copy-id user@master-ip

ssh-copy-id user@worker-ip


**If you face this error follow below steps.**

root@devops-tool:~# ssh-copy-id govadmin@172.16.106.54 /usr/bin/ssh-copy-id: ERROR: No identities found root@devops-tool:~# ssh-copy-id govadmin@172.16.106.55 /usr/bin/ssh-copy-id: ERROR: No identities found root@devops-tool:~#


Solution: Create an SSH key on the control node

You must generate one SSH key pair on devops-tool, then copy it to both servers.

🧱 Step 1: Generate SSH key (DO THIS ON Ansible Master)

Run as root (since you are root):

ssh-keygen -t rsa -b 4096

Step 2: Verify the key exists

Run:

ls -l /root/.ssh/

Step 3: Copy the key to both Kubernetes nodes

Now retry ssh-copy-id.

Master node

ssh-copy-id govadmin@172.16.106.54

Worker node

ssh-copy-id govadmin@172.16.106.55


You’ll be asked one last time for the password of govadmin. After this, no password will be needed again.


Step 4: Test passwordless SSH (VERY IMPORTANT)

Run:

ssh govadmin@172.16.106.54

ssh govadmin@172.16.106.55

🧪 Next validation command (run AFTER SSH works)

ansible -i inventory.ini all -m ping

Expected output:

master | SUCCESS => {"ping": "pong"}

worker | SUCCESS => {"ping": "pong"}


















