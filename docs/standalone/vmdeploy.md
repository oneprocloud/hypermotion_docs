

---

?>  <font face="黑体" size=4  color=red>* 安装步骤导览：</font> </br></br>
1.安装**迁移主控台「HyperMotion」**：使用下载的[qcow2镜像](https://oneprocloud.oss-cn-beijing.aliyuncs.com/download/HM_IMG-191227-2020-09-02.qcow2)进行安装部署，此处建议安装在阿里云平台主机；</br>
2.安装**云端数据代理「HyperGate」**：使用下载的[qcow2镜像](https://oneprocloud.oss-cn-beijing.aliyuncs.com/download/HM_IMG-191227-2020-09-02.qcow2)进行安装部署，需安装在阿里云平台主机；</br>
3.创建 **驱动适配镜像「HyperDoor」**：该镜像用于迁移主机迁移至阿里云后的驱动自适配，利用「HyperGate」实例复制一个镜像即可。  </br>



---
## 1. 创建实例，命名为「HyperMotion」

使用上传的镜像启动一台实例，实例配置要求如下：</br>

参数  | 含义
------------- | -------------
源类型  | 请选择上一步所上传的镜像源
CPU  | 建议4-Core，最低2-Core
RAM | 建议8GB，最低4GB
OS Disk  | 建议100GB，最低40GB
安全组  | 已开放22、18088、18766、10080端口号的安全组


## 2. 自动安装部署界面

!> 默认选择 **「HyperMotion+Proxy」**即可，其他选项用于分布式部署使用，没有特殊需求，均使用第一项即可


进入实例控制台界面，自动进入以下界面，'Enter'键入下一步，

![5.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/63.png ':size=70%')

系统自动部署完成

?> 系统部署完成，按照页面提示通过Chrome或火狐浏览器打开进行配置使用

![6.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/7.png ':size=70%')

----

## 3. 迁移主控平台管理

HyperMotion主控平台部署完成之后，可以通过以下认证信息登陆虚拟机Console进行管理，登陆信息如下:</br>

**登录名：<u>operator</u>**</br>
**登录密码：<u>P@ssw0rd</u>**</br>

!> 注：1. 首次登陆后需强制修改密码，密码要求：大小写字母加数字，8位以上；</br>
 &ensp; &ensp; &ensp;2. 如需切换root用户，执行sudo su root命令；

![img](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/3.png ':size=80%')
