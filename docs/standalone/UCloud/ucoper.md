---


[confwiz.md](../confwiz.md ':include')


## 4. UCloud连接设置

**1. 配置向导进入‘目标端平台配置’界面，选择UCloud图标**

![43.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image018.png ':size=90%')

**2. 填写云平台认证信息后点击【下一步】**

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image019.png ':size=90%')

?> 需要填写目标云端认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 目标云平台已安装HyperGate虚机IP地址，需与HyperMotion、UCloud互通
云平台服务端口  | 默认的服务端口为18090
公钥 | UCloud的API公钥ID (详情参见附录 UCloud平台认证信息获取)
私钥 | UCloud的API私钥ID (详情参见 附录 UCloud平台认证信息获取)
项目ID | 详情参见 附录 UCloud平台认证信息获取
地域ID | 选择安装HyperGate虚机所在地域（例：北京二 上海二）

?> 需要填写相关地域、可用区以及镜像ID信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：北京二 上海二）
可用区ID  | 选择安装HyperGate虚机所在区域 （北京二-可用区B 北京二-可用区C）
镜像ID | 本地上传至UCloud的镜像ID（详情参见附录 UCloud平台认证信息获取）

**3. 配置向导完成**

密码修改完成后，重新登陆，确认配置信息无误后配置向导完成 

![45.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image022.png ':size=90%')
