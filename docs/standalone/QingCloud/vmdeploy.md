

---

?>  <font face="黑体" size=4  color=red>* 安装步骤导览：</font> </br></br>
1.安装**迁移主控台「HyperMotion」**：使用下载的**「[qcow2镜像](standalone/aliyun/premise.md?id=qcow2下载)」**进行安装部署，此处建议安装在源端平台主机；</br>
2.安装**云端数据代理「HyperGate」**：使用ISO镜像进行推送安装，无需下载镜像，需部署在青云平台主机；</br>
3.制作 **驱动适配镜像「HyperDoor」**：因青云暂不支持自定义镜像的上传，需在目标端青云平台制做一个镜像主机再转化为镜像文件；镜像主机scp上传在源平台的镜像源（Livecd_HyperDoor_<date>.qcow2）并部署在青云平台。  </br>


!> 此HyperMotion主控平台安装步骤以VMware平台安装作为展示，其他QCOW2镜像方式安装均一致，无需过多配置


---

## 1. 创建虚拟机，命名为「HyperMotion」

使用上传的镜像启动一台虚拟机，虚机或实例配置要求如下：</br>

参数  | 含义
------------- | -------------
源类型  | 请选择上1步所上传的镜像源
CPU  | 建议4-Core，最低2-Core
RAM | 建议8GB，最低4GB
OS Disk  | 建议100GB，最低40GB

## 2. 设置网络

!> 网络配置内容仅出现在安装的虚拟机本地网卡没有配置IP地址时，将会提示配置相关网络信息，如果虚拟机网卡已经自动获取IP地址，将不会出现以下步骤

进入虚机或实例控制台界面，自动进入以下界面，
请根据实际情况填写框内信息，'Enter'键入下一步，

![4.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/4.png ':size=40%')

## 3. 自动安装部署界面

!> 默认选择 **「HyperMotion+Proxy」**即可，其他选项用于分布式部署使用，没有特殊需求，均使用第一项即可


进入虚机或实例控制台界面，自动进入以下界面，'Enter'键入下一步，

![5.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/5.png ':size=40%')

系统自动部署完成

?> 系统部署完成，按照页面提示通过Chrome或火狐浏览器打开进行配置使用

![6.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/7.png ':size=70%')

----

## 4. 迁移主控平台管理

HyperMotion主控平台部署完成之后，可以通过以下认证信息登陆虚拟机Console进行管理，登陆信息如下:</br>

**登录名：<u>operator</u>**</br>
**登录密码：<u>P@ssw0rd</u>**</br>

!> 注：1. 首次登陆后需强制修改密码，密码要求：大小写字母加数字，8位以上；</br>
 &ensp; &ensp; &ensp;2. 如需切换root用户，执行sudo su root命令；

![img](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/3.png ':size=80%')
