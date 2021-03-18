

---
## 1. 创建实例，命名为 HyperGate

!> 注：1. 此步骤操作请在目标端AWS上进行操作；</br>
 &ensp; &ensp; &ensp;2. 部署方式及参数要求请参照[ 附录 创建HyperGate实例](https://docs.oneprocloud.com/#/Appendix?id=_22-aws) 的说明。
 

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


!> 注：-i指定HyperGate IP  ；-u指定HyperGate用户，建议使用管理员用户 ；-k若使用秘钥连接，可指定私钥文件路径。 </br>   

**2. 等待HyperGate安装完成，安装完成如下图**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/13.png ':size=90%')



**3. 装完成后需重启HyperGate主机保证数据落盘**

---
## 3. 创建「Linux  HyperDoor」镜像

**1. 关闭HyperGate实例，选择该实例→【操作】→【映像】→【创建映像】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/14.png ':size=90%')


**2. 填写自定义镜像名称等信息后选择【创建】，创建后在映像列表中查阅镜像ID**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/15.png ':size=90%')


---


## 4. 创建「Windows  HyperDoor」镜像


**1. 创建一台Windows 2019的实例，并修改实例登录密码**

!> 注：请务必修改root账号登录密码为bofei123 ，以便自动连接进行驱动修复。 </br>       



**2. 创建后关闭实例，同样的方法创建Winodws HyperDoor镜像**

**3. 创建后同样在映像列表中查阅镜像ID**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/16.png ':size=90%')


