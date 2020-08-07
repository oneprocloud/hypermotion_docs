## 连接阿里云 

1. 返回概览界面，点击目标云平台连接中的【阿里云】图标，

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/12.png ':size=80%')

2. 进入目标端连接界面,根据安装步骤操作

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/13.png ':size=80%')

 ---
### 安装部署HyperGate

1. 创建一台实例，命名为<**HyperGate**>

!> 注：1. 此步骤操作请在目标端阿里云平台上进行操作</br>
2.部署方式请参照VMware文档中[部署OVF模板]([链接地址](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html)) 的说明

2. 登陆<HyperGate>实例主机，复制并执行以下命令:

```
curl https://download.oneprocloud.com/softwares/getdocker.sh |sudo bash
```

![14.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/14.png ':size=80%')

3. 复制并执行以下命令，完成部署

```
curl https://download.oneprocloud.com/softwares/gethypergate.sh |sudo bash
```

![15.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/15.png ':size=80%')

4. 安装阶段步骤完成后点击【下一步】按钮，

### 填写云平台认证信息

1. 填写目标云平台相关认证信息，AK/SK等

![16.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/16.png ':size=80%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与阿里云互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录二 阿里云平台认证信息获取)
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录二 阿里云平台认证信息获取)
API接入地址 | 默认 ecs.aliyuncs.com

2. 填写目标云平台相关地域信息

![17.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/17.png ':size=80%')

?> 需要填写的信息说明

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：华北、华东、香港）
可用区ID  | 选择安装HyperGate虚机所在区域 （如华北1可用区B  华北1 可用区C）
镜像ID | 创建的阿里云的镜像ID（详情参见附录二 阿里云平台认证信息获取）

3. 填写完成后点击【完成】按钮，系统提示"创建目标端存储成功"，同时可在【设置】→【目标平台设置】中查看连接情况。

![18.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/18.png ':size=80%')
 
