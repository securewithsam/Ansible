### Creating Inventory File for Remote Hosts)
```sh
sudo nano /etc/ansible/hosts
```
### Enter below and save
```sh
[servers]
192.168.0.112
192.168.0.113
192.168.0.114


 [servers:vars]
 ansible_user=infra-admin
 ansible_port=2022
 ansible_become=yes
 ansible_become_method=sudo
 ansible_python_interpreter='/usr/bin/python3'
```

### Create a playbook 
```sh
nano update.yml
```
```sh
- hosts: servers
  tasks:
    - name: Update cache 
      apt:
       update_cache: yes
         
    - name: Upgrade all packages on servers
      apt: 
        name: "*"
        state: latest
```        


### Run the playbook 
```sh
ansible-playbook update.yml -bK
```
