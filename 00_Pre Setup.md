Please check MAC address for public and internal cards

<br>

## Information
<br>

**Master**\
Hostname: master\
enp0s3: private(internal) network 192.168.1.254\
enp0s8: public network 192.168.11.6

**Compute1**\
Hostname: c1\
enp0s3: private network 192.168.1.253 MAC 08:00:27:99:b3:4f

<br>

### Add master host
```
# vi /etc/hosts

192.168.1.254 master
```

```
hostnamectl set-hostname master
```

### Disable firewall
```
# systemctl disable firewalld
# systemctl stop firewalld
```

### Disable selinux
```
# vi /etc/selinux/config

SELINUX=disabled
```

### Reboot master node 
```
# reboot
```

### Update CentOS
```
# yum -y update
```
