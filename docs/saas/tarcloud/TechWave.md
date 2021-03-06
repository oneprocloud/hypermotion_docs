
 ---
1. 左侧菜单栏【设置】→【目标平台设置】，选择‘华为云（公有云）’图标，

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/8.png ':size=90%')


2. 进入目标端连接界面,根据安装步骤操作

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/2.png ':size=90%')

---

### 1.安装部署**HyperGate**


1. 创建一台实例，命名为**HyperGate**

!> 注：1. 此步骤操作请在目标端华为云上进行操作;</br>
 &ensp; &ensp; &ensp;2. 部署方式及参数要求请参照[附录 创建HyperGate实例](Appendix/HyperGate?id=_25-华为云（公）)的说明。
 
?> 安装之前请在华为云平台账号下确认以下信息：</br>
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

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/3.png ':size=90%')

3. 复制并执行以下命令，完成部署

```
curl https://download.oneprocloud.com/softwares/gethypergate.sh |sudo bash
```

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/4.png ':size=90%')

4. 安装阶段步骤完成后点击【下一步】按钮，


 ---

### 2.填写云平台认证信息

1. 填写目标云平台相关认证信息，AK/SK等

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/5.png ':size=90%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与华为云互通
云平台服务端口  | 默认的服务端口为18090
云账号 | 华为云登陆时的账号名
用户  | 华为云登陆时的用户名
密码 | 华为云登陆时的用户密码
地域ID | 选择安装云平台服务虚机所在地域（例：华北、华东、香港）
可用区ID | 选择安装云平台服务虚机所在可用区

2. 填写目标云平台相关地域信息

![17.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/6.png ':size=90%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
云平台项目 | 默认 cn-north-1
镜像ID | 本地上传至华为云的镜像ID（详情参见[附录 华为云平台认证信息获取](Appendix/access?id=_45-华为云（公）))


3. 填写完成后点击【完成】按钮，系统提示"创建目标端存储成功"，同时可在【设置】→【目标平台设置】中查看连接情况。

![17.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/huawei/7.png ':size=90%')