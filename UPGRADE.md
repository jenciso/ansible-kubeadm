## UPGRADE

Control Plane

```
sudo yum install -y kubeadm-1.18.14-0 --disableexcludes=kubernetes
kubeadm upgrade apply v1.18.14
```


Nodes
```
sudo yum install -y kubeadm-1.18.14-0 --disableexcludes=kubernetes
sudo kubeadm upgrade node
sudo yum install -y kubelet-1.18.14-0 kubectl-1.18.14-0 --disableexcludes=kubernetes
sudo systemctl daemon-reload && systemctl restart kubelet
```
