

---
## 1. 创建实例，命名为「HyperGate」

!> 注：1. 此步骤操作请在目标端Azure上进行操作；</br>
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




