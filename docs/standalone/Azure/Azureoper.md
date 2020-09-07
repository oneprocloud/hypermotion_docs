---
[confwiz.md](../confwiz.md ':include')

---

## 4. Azure连接设置

**1. 配置向导进入‘目标端平台配置’界面，选择AWS图标**

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/17.png ':size=90%')

**2. 填写云平台认证信息后点击【下一步】**

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/18.png ':size=90%')

?> 需要填写目标云端认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与AWS互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录二 AWS平台认证信息获取)
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录二 AWS平台认证信息获取)
API接入地址 | 默认 ecs.aliyuncs.com

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/19.png ':size=90%')

?> 需要填写相关地域、可用区以及镜像ID信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：北京、宁夏）
可用区ID  | 选择安装HyperGate虚机所在区域 （例：北京1 可用区A）
Linux 镜像ID| 本地上传至AWS的Linux ID（详情参见附录三 AWS平台认证信息获取）
Windows 镜像ID| 本地上传至AWS的Windows ID（详情参见附录三 AWS平台认证信息获取）

**3. 配置向导完成**

目标平台配置信息填写完成后，点击【下一步】，确认配置信息无误后配置向导完成，系统提示修改密码后重新登录。

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/20.png ':size=90%')