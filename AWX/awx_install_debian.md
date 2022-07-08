# INSTALL AWX ON DEBIAN :

```sh
apt-get update -y
apt-get install apt-transport-https ca-certificates software-properties-common unzip gnupg2 curl git -y

echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu bionic main" | tee /etc/apt/sources.list.d/ansible.list

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367

apt-get update -y
apt-get install ansible -y
```

# Install Docker:

```sh
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update
```

# Install Docker Compose:

```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

# Install Node.js and NPM

```sh
apt-get install nodejs npm -y
npm install npm --global

apt-get install python3-pip git pwgen -y
pip3 install docker-compose==1.28.5
```

# Install AWX

```sh
wget https://github.com/ansible/awx/archive/17.1.0.zip
unzip 17.1.0.zip
cd awx-17.1.0/installer/
pwgen -N 1 -s 30
nano inventory
[update below]

admin_user=admin
admin_password=securepassword
secret_key=[generated with line 47 above]

cd /usr/local/bin/
chmod +x docker-compose

ansible-playbook -i inventory install.yml
```

http://your-server-ip
