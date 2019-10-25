## UPGRADE

Control Plane

```
yum install -y kubeadm-1.15.5-0 --disableexcludes=kubernetes
sudo kubeadm upgrade plan
```


Nodes
```
yum install -y kubeadm-1.15.5-0 --disableexcludes=kubernetes
sudo kubeadm upgrade node
yum install -y kubelet-1.15.5-0 kubectl-1.15.5-0 --disableexcludes=kubernetes
systemctl daemon-reload
sudo systemctl restart kubelet
```
