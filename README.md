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
(To be update soon)