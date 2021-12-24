# Kubernets_vnk8071

"Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications."

Source: https://www.youtube.com/watch?v=X48VuDVv0do

## Install
On linux:
- Install minikube
```bash
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```

- Install kubectl
```bash
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
```
Or you can run
```bash
bash setup-linux.sh
```

On Mac:
- Install minikube, kubectl also install (Dependency)
```bash
brew update
brew install minikube
```

Minikube require hypervisor:
- KVM
- VirtualBox
- Hyperkit
- Docker 

*Note*: Recommend to use Docker drive. (Easy for setup)

## Activate minikube
Run:
```bash
minikube start --vm-driver=docker
```
I used docker driver, you can change vm-driver you installed before.

Or you can run without vm-driver by
```bash
minikube start --vm-driver=none
```
## Structure of minukube
1. Node: It contain pod and database.
- Simple server.
- Physical or virtual machine.

2. Pod: 
- Abstraction over container. 
- It is the smallest unit in Kubernetes and familiar with docker containers or container images. 

3. Service: Static or permanent IP address.

4. Ingress: The request of user goes first to ingress and then forward to the service.

5. Config map: External configuration.

6. Secret: Likely config map. It's used to store secret data, username, password. 

7. Volume:
- Storage on local machine.
- Remote outside of the K8s cluster.

8. Deployment: Create replicas to mantain pod and database.

## Flow
First create config map yaml file:
```bash
Ex: scripts/mongodb-configmap.yaml
```

Then create secret yaml file:
```bash
Ex: scripts/mongodb-secret.yaml
```
Find user and password encode:
```bash
echo -n <name>user | base64
echo -n <name>password | base64
```

Final create deployment and service yaml file
```bash
Ex: scripts/mongodb-deploy.yaml
```
- Change the number of replicas to maintain pod and database.

- Deploy for many pods by using labels:
```bash
metadata:
    labels:
        app: <name>
```

## Deploy
Use Kubectl to run with command line.

Check current pod | deployment | service
```bash
kubectl get pod
and 
kubectl get deployment
and 
kubectl get service
```

Apply manages applications by:
```bash
kubectl apply -f scripts/mongodb-configmap.yaml
```
Then do the same with secret and deployment yaml file.

Check all apply:
```bash
kubectl get all
```

Final, get ip of minikube and external port to open browser of demo deploy.
```bash
minikube ip
kubectl get scv
```

Open browser with minikube_ip:external_port.

## Let's try.
