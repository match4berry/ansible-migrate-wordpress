# Ansible playbook for building up Wordpress Site

### Requirements
- Ansible 2.9 or newer running on Ubuntu 20.04 (might work with newer Ubuntu as well)
- Ubuntu 20.04 server configured so that you can use ssh
- any wordpress site as tar (make sure that when extracting the tar, it extracts all files not one folder which contains files)[this should work with any preinstalled wordpress site]
- mysqldump of wordpress site (existing) wordpress installation as .sql

### 1. What is this
This playbook can be used with any pre installed wordpress sites. This repository could be used when we need to migrate personal website to another server.

### 2. What this does
This playbook makes it easy to build up site in Ubuntu 20.04 server.

It will take care of following things:

 - Update OS
 - Install / Harden SSH
 - Install / Harden Firewall with iptables
 - Install NGINX
 - Install MySQL
 - Migrate wordpress site
 - Migrate database site
 
### 3. Running

 - Specify hostname of your server into hosts file
 - Specify hostname of the site in: group_vars/all
 - Specify path of the existing wordpress tar and mysqldump in: group_vars/all
 - MAKE SURE that all other configs are ok in group_vars/all
 - MAKE SURE that you can say "ssh hostname" and it will login without password/user prompt
 - cd to same path where this README.md is located
 - Run: ansible-playbook migrate.yml -i hosts --extra-vars "ansible_sudo_pass=ínsertpasshere"

### 4. Credits
https://github.com/tucsonlabs/ansible-playbook-wordpress-nginx
https://github.com/mikegleasonjr/ansible-role-firewall
