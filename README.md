## Ansible Playbook to provision kubeadm

Provision VM's

```
./new-vm.sh -n k8s-master -m 2048 -c 2 -i 192.168.122.100
./new-vm.sh -n k8s-node01 -m 2048 -c 2 -i 192.168.122.101
```

Install 
```
ansible-playbook site.yml -i inventory
```

Setup Master

```
kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address $(hostname -i)
```


Install calico networking provider

```
kubectl apply -f https://docs.projectcalico.org/v3.10/manifests/calico.yaml
```
