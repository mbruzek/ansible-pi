# ansible-pi
This is a project to model all the tasks that need to be done for a
Raspberry Pi with a default image.

# Prerequisites
1. You have some Raspberry Pis that are running the Raspbian image that are
accessible via ssh on your network.
2. You have this complete repository on your host system, and you have Ansible
installed.
```sh
git clone https://github.com/mbruzek/ansible-pi.git
cd ansible-pi
```
3. Edit the `inventory` file to contain the IP addresses or hostnames
of the Raspberry Pi systems in the group "raspberrypis".

4. Create an Ansible vault file for the `wifi_ssid`, `wifi_password`, and
`new_password` variables. Then create a plain text file with the password used
to create the vault.
```sh
ansible-vault create roles/raspbian/vars/secrets.yml
vi password-file.txt
```

# Usage
Run the `playbook.yml` with the `ansible-playbook` command and the
`--vault-password-file` flag:
```sh
ansible-playbook playbook.yml --vault-password-file password-file.txt
```
For more information on what tasks are performed, read the
[role tasks](roles/raspbian/tasks/main.yml).
