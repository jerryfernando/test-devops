# Terraform,Ansible, and aws cli

## isntall Terraform 
sudo nano/vim instal_terraform.sh

```
#!/usr/bin/env bash

sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
wget -O- https://apt.releases.hashicorp.com/gpg | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
gpg --no-default-keyring \
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
--fingerprint
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt-get install terraform
```

sudo chmod +x install_terraform.sh

./install_terraform.sh

## install ansible
sudo nano/vim install_ansible.sh
```
#!/usr/bin/env bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```
sudo chmod +x install_ansible.sh

./install_ansible.sh

## install aws cli
sudo nano/vim install_awscli.sh
```
#!/usr/bin/env bash

sudo apt-get install unzip -y
sudo apt-get install python3.10-venv -y
curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
unzip awscli-bundle.zip
sudo /usr/bin/python3.10 awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
```
sudo chmod +x install_awscli.sh

./install_awscli.sh

