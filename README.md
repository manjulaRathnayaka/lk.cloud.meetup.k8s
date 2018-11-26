# Private Cloud Discussion - Kubernetes on Your Local Machine

This is to share cloud meetup demo artifacts and instructions to get an overview of docker, k8s and minikube.   
    
**Prerequisites**
  
1. OS - Ubuntu 18.04   
2. Docker
```bash
    sudo apt install apt-transport-https ca-certificates curl software-properties-common 
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt update 
    sudo apt install docker-ce 
    sudo systemctl status
    docker docker -v
```
3. Hypervisor - VirtualBox      
```bash
    sudo apt install virtualbox virtualbox-ext-pack
```      
4. Minikube  
```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    chmod +x minikube-linux-amd64 
    sudo mv minikube-linux-amd64 /usr/local/bin/minikube
``` 
5. Kubectl
```bash
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x ./kubectl   
    sudo mv ./kubectl /usr/local/bin/kubectl
```
**Demo Steps**
1. [To package a tomcat application as a docker image](https://github.com/manjulaRathnayaka/lk.cloud.meetup.k8s/tree/master/docker)
2. [To run k8s cluster in your local machine](https://github.com/manjulaRathnayaka/lk.cloud.meetup.k8s/tree/master/minikube)
3. [To demonstrate rolling updates with zero down time](https://github.com/manjulaRathnayaka/lk.cloud.meetup.k8s/tree/master/k8s)
