# Ansible Playbooks for Server Configuration
This repository contains a collection of Ansible playbooks and configuration files to automate the setup and configuration of a server. Below is a brief description of each file and its purpose.

`00_main.yml`
- This is the main Ansible playbook file that includes all the other playbook files in the desired order. It serves as the entry point for executing the entire server configuration.

`01_check_connection.yml`
- This playbook checks the SSH connectivity to the target server to ensure that Ansible can establish a connection.

`02_install_mysql.yml`
- This playbook installs the MySQL database server on the target server.

`03_database_user.yml`
- This playbook creates a new user and database in MySQL. It prompts for the desired username, password, and database name during execution.

`04_install_php.yml`
- This playbook installs PHP 8.1 on the target server.

`05_install_nginx.yml`
- This playbook installs the Nginx web server on the target server.

`06_download_adminer.yml`
- This playbook downloads and sets up the Adminer database management tool.

`07_nginx-default_overwrite.yml`
- This playbook overwrites the default Nginx configuration file with a custom configuration specific to adminer access with IP/*.php needs.

`08_restart_FPM-Nginx.yml`
- This playbook restarts the PHP-FPM and Nginx services to apply the configuration changes and update the upgrade the value of 
`upload_max_filesize` & `post_max_size` & `memory_limit` after restart php fpm. 

`default`
- The default file is a sample Nginx configuration file that can be used as a starting point for your specific server configuration. You can modify it as needed to serve your application.

Please note that before executing these playbooks, you should update the necessary variables and configurations according to your environment and requirements.

# Pre-installation 

- For the create MySQL related user on the target server need to install it in the machine where you are performing this Ansible file.

```
ansible-galaxy collection install community.mysql
```

# Ansible-Hosts file

The /etc/ansible/hosts file is the inventory file used by Ansible to define and organize the hosts (remote servers) that Ansible will manage. It is a text file that lists the hostnames or IP addresses of the remote servers and organizes them into groups.

```
# Ansible-Target-Server
[test]
3.109.157.245 ansible_ssh_private_key_file=/home/$USER/.ssh/id_rsa
```