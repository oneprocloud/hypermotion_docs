
 ---
1. 返回概览界面，点击目标云平台连接中的【UCLoud】图标，

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image043.png ':size=90%')


2. 进入目标端连接界面,根据安装步骤操作

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image013.png ':size=90%')


### 1.安装部署**HyperGate**


1. 创建一台实例，命名为**HyperGate**

!> 注：1. 此步骤操作请在目标端UCLoud上进行操作;</br>
 &ensp; &ensp; &ensp;2. 部署方式及参数要求请参照[ 附录一 创建HyperGate实例](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html) 的说明。
 
?> 安装之前请在UCloud平台账号下确认以下信息：</br>
**（1）账户权限开通：**</br>
	   Server Administrator（管理ECS实例用于创建HypereGate实例）</br>
       IMS Administrator（管理镜像用于创建HyperDoor镜像）</br>
       VPC Administrator（管理VPC用于放行端口）</br>
	- 如该账号为主账号，默认已赋予以上权限，请跳过此步骤；</br>
	如以上权限未开放，请参考华为文档中子用户权限设置中有关为RAM用户、用户组分配授权策略的说明;</br>
	如需自定义权限策略，请参照附件三 【自定义权限管理策略】自定义权限策略后再授予权限;</br>
**（2）预定实例安装所在地域下已创建专有网络VPC和交换机;**</br>
-如未创建专有网络VPC和交换机，请参考华为文档中创建VPC网络中创建VPC的说明;</br>
**（3）预定实例安装所在地域下已创建安全组，并已放行端口12222/18090/3260/22;**</br>
	如未创建安全组或未放行以上端口，请参考华为文档中创建安全组中的说明。</br>

2. 登陆<HyperGate>实例主机，复制并执行以下命令:

```
curl https://download.oneprocloud.com/softwares/getdocker.sh |sudo bash
```

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image014.png ':size=90%')

3. 复制并执行以下命令，完成部署

```
curl https://download.oneprocloud.com/softwares/gethypergate.sh |sudo bash
```

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image015.png ':size=90%')
4. 安装阶段步骤完成后点击【下一步】按钮，


 ---

### 2.填写云平台认证信息

1. 填写目标云平台相关认证信息，AK/SK等

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image016.png ':size=90%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 目标云平台已安装HyperGate虚机IP地址，需与HyperMotion、UCloud互通
云平台服务端口  | 默认的服务端口为18090
公钥 | UCloud的API公钥ID (详情参见附录 UCloud平台认证信息获取)
私钥  | UCloud的API私钥ID (详情参见 附录 UCloud平台认证信息获取)
项目ID | 详情参见 附录 UCloud平台认证信息获取
地域ID | 选择安装HyperGate虚机所在地域（例：北京二 上海二）

2. 填写目标云平台相关地域信息

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/UCloud/image017.png ':size=90%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
地域ID | 选择安装HyperGate虚机所在地域（例：北京二 上海二）
可用区ID | 选择安装HyperGate虚机所在区域 （北京二-可用区B 北京二-可用区C）
镜像ID | 本地上传至UCloud的镜像ID（详情参见附录 UCloud平台认证信息获取）

3. 填写完成后点击【完成】按钮，系统提示"创建目标端存储成功"，同时可在【设置】→【目标平台设置】中查看连接情况。

