# 迁移主控平台 - HyperMotion

## 上传安装介质

!> 本此HyperMotion主控平台安装以VMware平台安装作为展示，其他QCOW2镜像方式安装均一致，无需过多配置

?> VMware平台 **「[ISO镜像](standalone/aliyun/premise.md?id=ISO下载)」**下载，将下载的ISO镜像上传至VMware平台

## 创建虚拟机

使用上传的ISO镜像启动一台虚拟机，虚机或实例配置要求如下：</br>

字段  | 含义
------------- | -------------
vCenter IP 地址  | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码
同步节点 | 通过OVA导入的主机IP

## 设置网络

!> 网络配置内容仅出现在安装的虚拟机本地网卡没有配置IP地址时，将会提示配置相关网络信息，如果虚拟机网卡已经自动获取IP地址，将不会出现以下步骤

根据实际情况填写框内信息，'Enter'键入下一步，

![4.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/4.png ':size=50%')

## 选择安装部署角色

!> 此步骤选择 **「HyperMotion+Proxy」**即可，其他选项用于分布式部署使用，没有特殊需求，均使用第一项即可

![5.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/5.png ':size=50%')

## 系统自动部署完成

?> 系统部署完成，按照页面提示通过Chrome或火狐浏览器打开进行配置使用

![6.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/7.png ':size=50%')

## 迁移主控平台管理

HyperMotion主控平台部署完成之后，可以通过以下认证信息登陆虚拟机Console进行管理，登陆信息如下:</br>

**登录名：operator**</br>
**登录密码：P@ssw0rd**</br>

![img](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/install/3.png ':size=50%')
