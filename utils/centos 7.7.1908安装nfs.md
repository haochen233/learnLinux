1. 文件服务器端安装使用`yum install nfs-utils rpcbind`命令安装nfs-utils，rpcbind两个工具。使用文件服务器的客户端只需要安装`nfs-utils`即可。
2. 安装完成后，编写nfs服务器端的配置文件，编写命令为`vi /etc/exports`，使用`man exports`查看配置选项（即导出表）。

exports文件示例：
```
格式：dir ip段(多个option用逗号隔开)
示例1（不限制客户端IP，将/data/share目录允许任意客户端挂载）：/data/share *(option)
示例2(限制192.168.226.0/24网段的IP只读)：/data/share 192.168.226.0/24(ro)
```
3. 写好exports文件后，服务器接下来启动rpc服务`systemctl start rpcbind`然后可以使用`rpcinfo -p localhost`来查看nfs服务项在rpc服务器注册的端口列表。此时还没有启动nfs，所以接下来可以启动nfs
4. 使用`systemctl start nfs`启动nfs服务。然后再查看rpc服务器的注册端口列表，就能看到许多关于nfs的端口列表。

5. 使用`showmount -e nfs服务器地址`命令可以查看nfs服务器的导出表。如果能够查看到的话，说明服务端已经启动了。

6. 然后再客户端上创建一个目录（当然客户端要启动nfs服务），对nfs进行挂载，例如：
    ```
    nfs服务器地址为192.168.226.3，服务器nfs目录为/data/share，本地挂载目录为/share（此目录必须已经存在，且不能有任何文件或子目录）
    mount 192.168.226.3:/data/share /share
    ```
7. 客户端挂载好后，在此目录下创建一个文件，然后在服务器端就能看到客户端创建好的文件。