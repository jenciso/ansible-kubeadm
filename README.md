## Ansible Playbook to provision kubeadm

Provision VM's
```
./new-vm.sh -n k8s-master -m 2048 -c 2 -i 192.168.122.100
./new-vm.sh -n k8s-node01 -m 2048 -c 2 -i 192.168.122.101
```

Pre-install cluster using a playbook:
```
ansible-playbook site.yml -i inventory
```

Configure the control plane:

```
ssh centos@192.168.122.100
sudo su - 
```

```
kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address $(hostname -i)
```

Setup your credential:
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

Install calico networking provider

```
kubectl apply -f https://docs.projectcalico.org/v3.10/manifests/calico.yaml
```

Verify:
```
kubectl get nodes
kubectl get pods --all-namespaces
kubectl get pods --all-namespaces -o wide
```
