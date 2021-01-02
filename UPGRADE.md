## UPGRADE

Control Plane

```
sudo yum install -y kubeadm-1.15.5-0 --disableexcludes=kubernetes
sudo kubeadm upgrade plan
```


Nodes
```
sudo yum install -y kubeadm-1.15.5-0 --disableexcludes=kubernetes
sudo kubeadm upgrade node
sudo yum install -y kubelet-1.15.5-0 kubectl-1.15.5-0 --disableexcludes=kubernetes
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```
