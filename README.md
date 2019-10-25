## Ansible Playbook to provision kubeadm

Install kubeadm in master and nodes 

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
