

---
## 1. 创建实例，命名为 HyperGate

**1. 登录AWS‘管理控制台’，【服务】→【EC2】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/1.png ':size=90%')

**2. 点击【实例】→点击【启动实例】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/2.png ':size=90%')

**3. 选择AMI：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/3.png ':size=90%')


?> 配置参考以下内容

选项  | 选项填写
-----------------| -------------
操作系统   | centos7.3~7.5 64位（X86）



**4. 选择实例类型**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/4.png ':size=90%')


?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
系列  | 通用型
vCPU| 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB


填写完成后点击【下一步，配置实例】，

**5. 配置实例**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/5.png ':size=90%')

选择网络VPC，完成后点击【下一步，添加存储】

**6. 添加存储**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/6.png ':size=90%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
存储大小  | 通用型SSD 建议100G，最低40G



**7. 添加标签**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/7.png ':size=90%')

将实例命名为‘HyperGate’，完成后点击【下一步，配置安全组】



**8. 配置安全组**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/8.png ':size=90%')

选择放行了12222/18090/3260/22端口的安全组后点击【审核和启动】

**9. 审核**

检查创建信息，点击【启动】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/9.png ':size=90%')

**10. 创建成功，下载密钥对文件，查看IP信息并记录：**


![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/10.png ':size=90%')

---
## 2. 推送安装HyperGate

**1. 登录HyperMotion主机命令行终端，输入以下命令**

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
## 3. 创建Linux  HyperDoor镜像

**1. 关闭HyperGate实例，选择该实例→【操作】→【映像】→【创建映像】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/14.png ':size=90%')


**2. 填写自定义镜像名称等信息后选择【创建】，创建后在映像列表中查阅镜像ID**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/15.png ':size=90%')


---


## 4. 创建Windows  HyperDoor镜像


**1. 创建一台Windows 2019的实例，并修改实例登录密码**

!> 注：请务必修改root账号登录密码为bofei123 ，以便自动连接进行驱动修复。 </br>       



**2. 创建后关闭实例，同样的方法创建Winodws HyperDoor镜像**

**3. 创建后同样在映像列表中查阅镜像ID**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/16.png ':size=90%')

---
