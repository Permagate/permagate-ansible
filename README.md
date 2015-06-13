# Permagate Playbooks

This is a collection of playbooks and roles used by me to quickly setup a new environment. 

### How to Use

1. (Optional) Add your user as a sudoer without password.
2. Install [Ansible](http://docs.ansible.com/intro_installation.html).
3. Add the following lines to `/etc/ansible/hosts`.

```
[localhost]
127.0.0.1
```

4. Download the repository from [https://github.com/Permagate/permagate-ansible.git](https://github.com/Permagate/permagate-ansible.git)
5. Copy config/X.yml.template to config/X.yml. X is the name of the playbook you want to run. Change the configuration if needed (Most important is probably git.email and git.username)
6. Run any of the playbooks! It will differ a bit depending on whether you did step 1 or not.
  
  * Run `ansible-playbook -v development.yml` If you did Step 1.
  * Run `ansible-playbook -v development.yml --ask-become-pass` If you skipped Step 1. You'll be prompted to input your sudo password.

7. Make a coffee while you are waiting.

### Some important considerations post-run

* If mysql is installed, it will use the default root/null authentication for the root user. You need to change this by running `sudo mysql_secure_installation` yourselves.
* This will setup to local machine by default. You can easily use these playbooks for remote server by reconfiguring /etc/ansible/hosts. Then, open a playbook that you want to run. Change the host to your new machine.
