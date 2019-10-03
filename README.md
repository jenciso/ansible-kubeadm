## Ansible Playbook to provision kubeadm

Ansible Playbook 

```
ansible-playbook site.yml -i inventory
```

Master

```
kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address $(hostname -i)
```


