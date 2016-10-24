1: Ec2主机挂载选项

磁盘挂载/卸载

- 磁盘挂载

1. 到ec2服务下的Volumes标签中创建磁盘，注意与所挂载的主机在同一区
    创建磁盘可以从之前创建的snapshot（磁盘镜像）创建，使用时不需要再格式化。
    创建磁盘可以选择磁盘类型（ssd, magnetic），根据需要选择。
2. 新创建的磁盘，在Actions中选择attach（或者点击右键，选择attach），挂载到目标主机，记住挂载的磁盘设备名称 /dev/xxxx
3. 在目标主机：sudo fdisk -l 查看挂载的磁盘
4. 格式化磁盘：sudo mkfs.ext4 /dev/xxxx
5. 挂载磁盘： sudo mount /dev/xxxx <target_dir>，需要保证target_dir存在
6. 编辑 /etc/fstab文件，否则下次重启时挂载的磁盘不会被自动挂载
    加入(每列以tab键隔开):
     /dev/xxxx       <target_dir>      ext4    defaults,nofail         0          2
    具体参考:
     http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html

- 磁盘卸载
1. 首先必须在目标主机 umount 该磁盘
    umount <target_dir> 确保 target_dir 没有进程使用。
    查看占用进程：lsof | grep <target_dir>
2. 在控制台EC2界面Volume标签中，在目标磁盘Actions（或者右键）选择Detach，从目标主机卸载磁盘。
