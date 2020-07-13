exec:  
1. `vi /etc/sysconfig/network-scripts/ifcfg-ens33`

2. 修改**BOOTPROTO=dhcp**为**BOOTPROTO=static**

3. 添加

```shell
    GATEWAY=192.168.x.x  #网关地址
NETMASK=255.255.255.0
IPADDR=192.168.x.x #IPV4地址
DNS1= 192.168.x.x #等于网关地址
```
4. 保存后，执行`systemctl restart network` 
5. 使用`ip`查看IP地址是否正确，在`ping baidu.com`是否可以连接到外网。