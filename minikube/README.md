# lk.cloud.meetup.k8s*

This section contains example commands to work with minikube.

To start a k8s cluster in your local machine, 
```bash
	minikube start
	Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
```
To access dashboard to view k8s resources.
```bash
	minikube dashboard	
```
To get node ip 
```bash
	minikube ip	
``` 
To ssh to the k8s node 
```bash
	minikube ssh 
```
To access the k8s cluster logs 
```bash
	minikube logs	
```
To delete the minikube setup
```bash
	minikube delete
```
