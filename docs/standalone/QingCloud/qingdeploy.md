

---
## 1. 创建实例，命名为「HyperGate」

!> 注：1. 此步骤操作请在目标端青云上进行操作；</br>
 &ensp; &ensp; &ensp;2. 部署方式及参数要求请参照[ 附录 创建HyperGate实例](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html) 的说明。
 


---
## 2. 推送安装「HyperGate」

**1. 登录「HyperGate」主机命令行终端，输入以下命令**

```
~]# cd /opt/installer/auto_install/
~]# ls -l

```

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/11.png ':size=70%')

```
~]# python auto_deploy.py -t hypergate -i HyperGate_IP -u root -k key_path

```
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/12.png ':size=90%')


!> 注：1. -i指定HyperGate IP  ；-u指定HyperGate用户，建议使用管理员用户 ；-p指定HyperGate用户密码； </br> 
    &ensp; &ensp; &ensp; 2.如使用密钥连接 -k若使用秘钥连接，可指定私钥文件路径；-P指定SSH端口，默认使用22端口。 </br> 

**2. 等待HyperGate安装完成，安装完成如下图**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/13.png ':size=90%')



**3. 装完成后需重启HyperGate主机保证数据落盘**

---
## 3. 制作「HyperDoor」镜像

**1.创建一个用于制作镜像的主机，命名为‘HyperDoor’**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/7.png ':size=90%')

?> 配置内容填写参考：

字段  | 含义
------------- | ----------------------
映像版本  | CentOS 7.5 64位
CPU/内存 | >=1核1G
系统盘| >=20GB

**2.创建一个磁盘并挂载到主机下**

选择【存储】-【硬盘】-【创建】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/8.jpg ':size=90%')

返回磁盘列表页面，选择已创建的磁盘，选择【更多操作】-【加载硬盘到主机】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/9.png ':size=90%')

**3.获取HyperDoor镜像并拷贝（scp）至主机内**

将获取的名称为：Livecd_HyperDoor_<date>.qcow2的镜像文件拷贝至主机内

```
~]#qemu-img convert -f qcow2 -O raw Livecd-HyperDoor_<date>.qcow2 hd-0712.raw

```

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/10.png ':size=90%')

**4.过dd把hyperdoor raw文件导入vdc**

```
~]# dd if=hd-0712.raw of=/dev/vdc

```

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/11.png ':size=90%')

**5.备份VDC，产生一个备份snapshot**

选择【硬盘】-【创建备份】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/12.png ':size=90%')

**6.完成映像制作**

【备份】-鼠标右击弹出选项-【制作成新映像】，将映像名称命名‘HyperDoor’

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/13.png ':size=90%')

**7.获取镜像ID**

管理控制台页面，选择【镜像】，记录名称的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/14.png ':size=90%')