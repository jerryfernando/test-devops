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

## Create aws iam 

### 1.create iam users
![user](https://github.com/jerryfernando/test-devops/assets/23428256/7761fe64-253e-4820-b46f-95808797d789)

### 2.create and add policies
create permissions
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowS3Access",
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": "*"
        }
    ]
}
```
![policies](https://github.com/jerryfernando/test-devops/assets/23428256/d248a26c-7a0a-46fe-9a68-38b9ea8f7664)

### create Access keys
![ackey](https://github.com/jerryfernando/test-devops/assets/23428256/4cdd9127-a74e-461a-b150-60800ea50495)

### connect aws to local server
```bash
  aws configure
```
```
AWS Access Key ID [None]: 
AWS Secret Access Key [None]: 
Default region name [None]: 
Default output format [None]:
```

![aws configure](https://github.com/jerryfernando/Final-task/assets/23428256/a6a7863a-2a60-4c6a-9861-86bc8f22a6b2)

aws ec2 describe-instances
