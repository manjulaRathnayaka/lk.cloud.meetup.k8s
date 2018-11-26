# lk.cloud.meetup.k8s*

This section contains example commands to work with k8s.

To get details of the default k8s cluster, 
```bash
	kubectl get all --all-namespaces
	kubectl describe nodes
	kubectl logs kube-dns-86f4d74b45-fz5lf -c kubedns -n kube-system
	kubectl exec -it kube-scheduler-minikube -n kube-system /bin/sh
```
To deploy the demo web application in k8s cluster 
```bash
	kubectl run demo-web-app --image=manjula/lk.cloud.meetup.k8s.tomcat-app:1.0.0 --port 8080
	kubectl get all
	kubectl exec -it demo-web-app-5bbc7d78d8-2gnlh /bin/bash
		wget http://localhost:8080/DemoApp/	
```
To expose the demo web application to the host machine via k8s node port 
```bash
	kubectl expose deployment demo-web-app --type=NodePort --target-port 8080
	kubectl get all
	minikube service demo-web-app (http://192.168.99.100:30811/DemoApp/)
		
``` 
To scale the demo-web-app with multiple replicas 
```bash
	kubectl scale deployment/demo-web-app --replicas=2
	kubectl get all 
```
To roll out a change of the web application 
```bash
	watch -n 0.1 'curl -s http://192.168.99.100:30811/DemoApp/'
	watch -n 0.1 'kubectl get pods'
	kubectl set image deployment/demo-web-app demo-web-app=manjula/lk.cloud.meetup.k8s.tomcat-app:2.0.0	
```
To avoid failures during the deployment update due to server is not fully started 
```bash
	kubectl get deployment demo-web-app -oyaml > deployment.yaml
	update deployment.yaml with readinessProbe as below.
	      - image: manjula/lk.cloud.meetup.k8s.tomcat-app:2.0.0
       		readinessProbe:
                tcpSocket:
                 port: 8080
                initialDelaySeconds: 5
                periodSeconds: 10
	kubectl apply -f deployment.yaml
        watch -n 0.1 'curl -s http://192.168.99.100:30811/DemoApp/'
        watch -n 0.1 'kubectl get pods'
	kubectl set image deployment/demo-web-app demo-web-app=manjula/lk.cloud.meetup.k8s.tomcat-app:2.0.0	
```
