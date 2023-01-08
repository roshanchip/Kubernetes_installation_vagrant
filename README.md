# Kubernetes Installation on Ubuntu 22.04

### On the Kube master server

Initialize the cluster by passing the cidr value and the value will depend on the type of network CLI you choose.

```bash
sudo kubeadm init --apiserver-advertise-address=192.168.56.10 --pod-network-cidr=10.244.0.0/16
```

### Start using the cluster using current user

```bash
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### To set up the Calico network

```bash
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```

### Install metrics server

```bash
git clone https://github.com/mialeevs/kubernetes_installation_crio.git
cd kubernetes_installation_crio/
kubectl apply -f metrics-server.yaml

```
