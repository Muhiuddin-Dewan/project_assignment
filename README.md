# project_assignment 
## Task-1
### Installing Process:
#### Docker:
Set up Docker's apt repository:
```
sudo apt-get install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update
```
Install Docker Packages:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose
```
#### Jenkins:
Install Jenkins using docker-compose:

Step-1: Create a directory "Jenkins_Installation"

Step-2: Create "docker-compose.yaml" under the directory

Step-3: Run Docker compose file by using docker-compose up -d 
##### docker-compose.yml
```
version: '3'

services:

  jenkins:
  
    image: jenkins/jenkins
    
    ports:
    
      - "8080:8080"
      
    volumes:
    
      - jenkins-data:/var/jenkins_home
      
volumes:

  jenkins-data:
  
    driver: local
```    
Step-4: You can now access Jenkins from the browser

Step-5: You have to provide initial credentials of your jenkins. For this you have to login to the container like
below command:
```
        $ docker exec -it container_it/bin/bash
        You can find the password on the "/var/jenkins_home/secrets/" directory.
```
##### Install minikube and Kubectl
Install minikube:
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube start --driver=docker
```
Install Kubectl:
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install kubectl /usr/local/bin/kubectl

kubectl version --client -o json
```