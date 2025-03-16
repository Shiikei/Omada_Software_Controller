# Omada_Software_Controller
#To install Omada Software Controller 03-2025
#Based on : https://gist.github.com/OSCUK/3c76ccabe78b6d3ce479c6d885b9c065
# I have install this software controller on Proxmox with a container it's a ubuntu 24.10 with 2 vcpu and 4gb ram
![image](https://github.com/user-attachments/assets/42883a74-9325-4ac3-a8a9-48d3d52aee45)

#I took the last version of all packages

apt update &&  apt install openssh-server -y
apt update &&  apt install openjdk-17-jre-headless jsvc curl -y
apt -y install gnupg2

#following package last update can be found at https://pgp.mongodb.com/

curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc |  apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/8.0 multiverse" |  tee /etc/apt/sources.list.d/mongodb-org-8.0.list

#following package last update can be found at https://archive.ubuntu.com/ubuntu/pool/main/o/openssl/?C=M;O=D

wget https://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.24_amd64.deb
dpkg -i libssl1.1_1.1.1f-1ubuntu2.24_amd64.deb

apt update &&  apt install mongodb-org
systemctl start mongod.service
systemctl status mongod
systemctl enable mongod

#following package last update can be found at https://support.omadanetworks.com/fr-be/product/omada-software-controller/?resourceType=download
wget https://static.tp-link.com/upload/software/2025/202501/20250109/Omada_SDN_Controller_v5.15.8.2_linux_x64.tar.gz
tar zxvf Omada_SDN_Controller_v5.15.8.2_linux_x64.tar.gz
cd Omada_SDN_Controller_v5.15.8.2_linux_x64
bash ./install.sh
