---


[confwiz.md](../confwiz.md ':include')


## 4. 阿里云连接设置

**1. 配置向导进入‘目标端平台配置’界面，选择阿里云图标**

![43.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/43.png ':size=80%')

**2. 填写云平台认证信息后点击【下一步】**

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/44.png ':size=80%')

?> 需要填写目标云端认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与阿里云互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录 [阿里云平台认证信息获取](Appendix?id=_41-%e9%98%bf%e9%87%8c%e4%ba%91%ef%bc%88%e5%85%ac%ef%bc%89))
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录 [阿里云平台认证信息获取](https://docs.oneprocloud.com/#/Appendix?id=_41-%e9%98%bf%e9%87%8c%e4%ba%91%ef%bc%88%e5%85%ac%ef%bc%89))
API接入地址 | 默认 ecs.aliyuncs.com

?> 需要填写相关地域、可用区以及镜像ID信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：华北、华东、香港）
可用区ID  | 选择安装HyperGate虚机所在区域 （如华北1可用区B  华北1 可用区C）
镜像ID | 创建的阿里云的镜像ID（详情参见附录 [阿里云平台认证信息获取](https://docs.oneprocloud.com/#/Appendix?id=_41-%e9%98%bf%e9%87%8c%e4%ba%91%ef%bc%88%e5%85%ac%ef%bc%89))


**3. 配置向导完成**

1. 目标平台配置信息填写完成后，点击【下一步】，确认配置信息无误后配置向导完成，系统提示修改密码后重新登录

![45.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/45.png ':size=80%')
