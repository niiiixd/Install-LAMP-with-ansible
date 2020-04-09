# Install LAMP with ansible playbook

This playbook will install a LAMP environment (Linux, Apache, MySQL and PHP) on CentOS 7 machine.

### The playbook should serve as a base for you to create your own playbook and configuration.

## Connection Test
```
ansible [remote_host] -m ping -u remote_user
```
If you're able to get a "pong" reply back from your node(s), your setup works as expected.

# LAMP on CentOS
A virtualhost will be created with the options specified in the vars/main.yml variable file.

## Settings

* mysql_root_password: the password for the MySQL root account.
* app_user: a remote non-root user on the Ansible host that will own the application files.
* http_host: your domain name.
* http_conf: the name of the configuration file that will be created within Apache.
* http_port: HTTP port, default is 80.
* disable_default: whether or not to disable the default Apache website. When set to true, your new virtualhost should be used as default website. Default is true.
### 1. Customize Options
```
cd Install-LAMP-with-ansible
vim vars/main.yml
```
```
---
mysql_root_password: "mysql_root_password"
app_user: "nix"
http_host: "your_domain"
http_conf: "your_domain.conf"
http_port: "80"
disable_default: true
```
### 2. Run the Playbook
ansible-playbook -i [inventory file] -u [remote user] lamp_on_centos.yaml
