# project_assignment 
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
Install Jenkins Installation:

Step-1: First install Java
```
sudo apt install openjdk-11-jdk -y

```

Step-2: Installing Jenkins
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg

sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update

sudo apt install jenkins
```

Step-3: Now start Jenkins service
```
sudo systemctl start jenkins.service
```

Step-4: You can now access Jenkins from the browser

Step-5: You have to provide initial credentials of your jenkins. 

below command:
```
        You can find the password on the "/var/jenkins_home/secrets/" directory.
```

![Jenkins_brower](/images/image2.PNG)

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
![check_by_command](/images/image1.PNG)

