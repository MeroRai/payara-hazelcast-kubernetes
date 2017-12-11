# payara-hazelcast-kubernetes
Demonstration of Payara Micro using Hazelcast-Kubernetes plugin 

### Prerequisites 
#### This demonstration assumes:

1.	Minikube is installed and that you have also installed Kubectl, which is a command-line tool for Kubernetes. 
2.  Docker is installed. 
3. 	You have basic knowledge on Kubernetes, Docker and Hazelcast. 

### To run the demonstration
1. Edit the "hazelcast.xml" file to match your service name, label name and value.
2. Create service for the first instance by executing the folowing command:
```
$ kubectl create -f payaraMicroService.yaml
```
3. Create deployment for the first instance by executing the following command:
```
$ kubectl create -f payaraMicroDeployment.yaml
```
4. Create service for the second instance by executing the folowing command:
```
$ kubectl create -f payaraMicro2Service.yaml
```
5. Create deployemnt for the second instance by executing the following command:
```
$ kubectl create -f payaraMicro2Deployment.yaml
```
6.	Insert string “{data}” into the first instance using:
```
$ curl -H "Accept: application/json" -H "Content-Type: application/json" -X PUT -d "{data}" http://<NODE-IP-ADDRESS>:30001/rest-jcache/webresources/cache\?key\=test
```
7.	Use second instance to retrieve the added value using:
```
$ curl http://<NODE-IP-ADDRESS>:30002/rest-jcache/webresources/cache\?key\=test{data}%
```
