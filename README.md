## Ansible Playbook to provision kubeadm

Install kubeadm in master and nodes 

```console
ansible-playbook site.yml -i inventory
```

Setup Master

```console
kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address $(hostname -i)
```


Install calico networking provider

```
kubectl apply -f https://docs.projectcalico.org/v3.9/manifests/calico.yaml
```
