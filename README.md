# ansible-pi
This is a project to model the many tasks that need to be done for a
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

4. Create an Ansible vault file for the sensitive variables used in the tasks:
`wifi_ssid`, `wifi_password`, and `new_password` with the appropriate values.
Then create a plain text file with the password used to create the vault.
```sh
ansible-vault create roles/raspbian/vars/vault.yml  # You will be prompted for a vault password.
vi password-file.txt                                # Put the vault password in this file.
```

# Usage
Run the `playbook.yml` with the `ansible-playbook` command and the
`--vault-password-file` flag:
```sh
ansible-playbook playbook.yml --vault-password-file password-file.txt
```

# Playbook overview:

### Read in the variables from the vault file and do not log the values!

### Determine if the system has a wireless adapter.

### Render the wifi template only for systems with wireless adapters and wifi variables.

### Copy the local ssh key to the managed host.

### Set the timezone.

### Set the keyboard layout.

### Render a locale file with the LANG env variable from local host so the next task can read it.

### Set selections, remove generated, reconfigure and update locale.

### Change the password to new_password from the vault file.

### Update the package manager.

### Update the system packages to the latest version.

### Remove the unnecessary packages.

### Remove the downloaded packages.

### Update the Raspberry Pi firmware, this may require a reboot.

### Reboot the the managed host.

### Wait for the managed host to return.


For more information on what tasks are performed, read the raspbian
[role tasks](roles/raspbian/tasks/main.yml).
