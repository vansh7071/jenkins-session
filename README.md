# Sample_JavaApplication
 
 *************************
 Jenkins shell script
 *************************
 
#!/bin/bash

sudo apt update -y

sudo apt install default-jre -y

java -version

sudo apt update -y

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update -y

sudo add-apt-repository universe -y

sudo apt-get install jenkins -y

sudo service jenkins start

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

#sudo service jenkins status


------------------------------------------------------------------------------------------------------------------

***********************
docker.sh
***********************

#!/bin/bash
sudo apt update -y

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" -y

sudo apt update -y

apt-cache policy docker-ce -y

sudo apt install docker-ce -y

#sudo systemctl status docker

sudo chmod 777 /var/run/docker.sock

-------------------------------------------------------------------------------------------------------------------------
