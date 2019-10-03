## To provision

```
ansible -m shell -a "echo kube-master.10.0.5.31.xip.io > /etc/hostname" -u ansible centos
ansible -m shell -a "sed -i 's/^IPADDR=10.0.5.11$/IPADDR=10.0.5.31/' /etc/sysconfig/network-scripts/ifcfg-enp0s3" -u ansible centos
ansible -m shell -a "reboot" -u ansible centos
```

## To install kubeadm

```
ansible-playbook -i inventory site.yml
```

## To setup

```
kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address $(hostname -i)
```

## GITLAB RUNNER
https://stackoverflow.com/questions/54707598/how-to-customise-config-toml-on-kubernetes
https://gitlab.com/gitlab-org/gitlab-runner/issues/2578
