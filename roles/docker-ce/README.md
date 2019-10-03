## Docker CE Provision

### Requeriments

* 1 device disk /dev/sdb (~60GB)


### Notes

If you prefer lvm, then you need to set:
```
docker_lvm_storage: false
```

If your device to mount /var/lib/docker won't /dev/sdb, then change the variable:
```
docker_lvm_device: sdc
``` 
