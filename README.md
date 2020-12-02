## Ansible Playbook to provision kubeadm

Provision VM's
```shell
./new-vm.sh -n k8s-master -m 2048 -c 2 -i 192.168.122.100
./new-vm.sh -n k8s-node01 -m 2048 -c 2 -i 192.168.122.101
```

Pre-install cluster using a playbook:
```shell
ansible-playbook site.yml -i inventory
```

Configure the control plane:

```shell
ssh centos@192.168.122.100
sudo su - 
```

```shell
kubeadm init --pod-network-cidr=172.18.0.0/16 --apiserver-advertise-address $(hostname -i)
```

Setup your credential:
```shell
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

Install calico networking provider

```shell
curl -sSL -o calico.yaml https://docs.projectcalico.org/v3.10/manifests/calico.yaml
sed -i -e 's#value: "192.168.0.0/16"#value: "172.18.0.0/16"#' calico.yaml
kubectl apply -f calico.yaml
```

Verify:
```shell
kubectl get nodes
kubectl get pods --all-namespaces
kubectl get pods --all-namespaces -o wide
```

## NOTES

If you need to get the token bootstrap in order to join another node in the cluster, use this command:
```shell
kubeadm token create --print-join-command
```
