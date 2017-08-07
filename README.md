# ansible-pi
This is a project to model all the tasks that need to be done for a
Raspberry Pi with a default image.

# Prerequisites
1. You have some Raspberry Pis that are running the Raspbian image that are
accessible via ssh on your network.
2. You have the complete repository on your host system, and you have Ansible
installed.
```sh
git clone https://github.com/mbruzek/ansible-pi.git
```
3. Edit the `ansible-pi/inventory` file to contain the IP addresses or hostnames
of the Raspberry Pi systems.

# Usage
Run the `playbook.yml` with the `ansible-playbook` command:
```sh
cd ansible-pi
ansible-playbook playbook.yml
```
For more information on what tasks are performed, read the 
[role tasks](roles/raspbian/tasks/main.yml).
