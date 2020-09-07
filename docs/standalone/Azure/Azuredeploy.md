

---
## 1. 创建实例，命名为 HyperGate

**1. 登录Azure‘管理控制台’，【虚拟机】→【添加】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/1.png ':size=90%')

**2. 选择操作系统**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/2.png ':size=90%')

?> 配置参考以下内容

选项  | 选项填写
-----------------| -------------
操作系统   | centos7.3~7.5 64位（X86）


**3. 配置实例信息：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/3.png ':size=90%')



**4. 配置用户密码和入站端口规则：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/4.png ':size=90%')


?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
用户名  | centos7.3~7.5 64位（X86）



**5. 选择磁盘类型：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/5.png ':size=90%')




**6. 选择网络：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/6.png ':size=90%')




**7. 确认配置信息：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/7.png ':size=90%')


检查创建信息，点击【创建】


**8. 创建成功，查看IP信息并记录：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/8.png ':size=90%')



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


!> 注：1. -i指定HyperGate IP  ；-u指定HyperGate用户，建议使用管理员用户 ；-p指定HyperGate用户密码； </br> 
    &ensp; &ensp; &ensp; 2.如使用密钥连接 -k若使用秘钥连接，可指定私钥文件路径；-P指定SSH端口，默认使用22端口。 </br> 

**2. 等待HyperGate安装完成，安装完成如下图**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/13.png ':size=90%')



**3. 装完成后需重启HyperGate主机保证数据落盘**




