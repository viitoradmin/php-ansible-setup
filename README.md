# Ansible Playbook for PHP-Based Website Environment Setup
With the help of this Ansible playbook, a PHP-based website environment can be quickly set up on a fresh Linux server. This playbook automates the deployment process and installation processes by utilising the strength and adaptability of Ansible, assuring consistency and minimising manual setup efforts.

Note: Make sure to have SSH access to the target server(s) with the appropriate credentials for Ansible to connect and execute commands remotely.

By leveraging the power of Ansible, you can easily replicate and scale your PHP-based website environment across multiple servers with minimal effort. Enjoy the simplicity and efficiency provided by this playbook, ensuring a consistent and reliable setup for your web applications.

# Ansible Playbooks for Server Configuration
This repository contains a collection of Ansible playbooks and configuration files to automate the setup and configuration of a server. Below is a brief description of each file and its purpose.

## project-structure

```
.
├── 01_check_connection.yml
├── 02_install_mysql.yml
├── 03_database_user.yml
├── 04_install_php.yml
├── 05_install_nginx.yml
├── 06_download_adminer.yml
├── 07_nginx-default_overwrite.yml
├── 08_restart_FPM-Nginx.yml
├── default
└── README.md
```

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

## Run Locally
permission of file 

```
-rw-rw-r-- 1 $USER $USER 3013 Jul 4 15:38 *.yml
```

# Ansible-Hosts file

The /etc/ansible/hosts file is the inventory file used by Ansible to define and organize the hosts (remote servers) that Ansible will manage. It is a text file that lists the hostnames or IP addresses of the remote servers and organizes them into groups.

```
# Ansible-Target-Server
[test]
3.111.217.83 ansible_ssh_private_key_file=/home/$USER/.ssh/id_rsa
```

## **Warning**
Assuming you've gone so far as to get Ansible running and have downloaded these playbooks, you probably understand how this stuff works and how much damage it could do. But just in case, These playbooks will remove data, destroy accounts and wreak havoc if pointed to the wrong account. Please be careful, keep backups and read the code before running it.