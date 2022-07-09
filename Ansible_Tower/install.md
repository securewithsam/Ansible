# Ansible tower needs Centos 8 - 4Gb RAM  - 2/4vCPU

```sh
sudo yum update -y
``

```sh
sudo yum install wget tar
``

```sh
sudo wget https://releases.ansible.com/ansible-tower/setup-bundle/ansible-tower-setup-bundle-latest.tar.gz
``

```sh
sudo tar -xzvf ansible-tower-setup-bundle-latest.tar.gz
``

```sh
cd ansible-tower-setup-bundle-3.8.6-2/
```

```sh
sudo vim inventory
``

[update below]

admin_password='Admin@123'
pg_password='Admin@123'


```sh
sudo vim /roles/preflight/defaults/main.yml
``

[change required_ram: 2048 ]

```sh
cd
cd ansible-tower-setup-bundle-3.8.6-2/
``

```sh
sudo ./setup.sh
``

# https://xx.xx.xx.xx
Login :
admin/Admin@123
