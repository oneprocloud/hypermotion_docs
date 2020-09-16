---


[confwiz.md](../confwiz.md ':include')


## 4. OpenStack连接设置

**1. 配置向导进入‘目标端平台配置’界面，选择OpenStack图标**

![43.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/8.png ':size=90%')

**2. 填写云平台认证信息后点击【下一步】**

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/9.png ':size=90%')

?> 需要填写目标云端认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 目标云平台已安装HyperGate的虚机IP地址
云平台服务端口  | 默认的服务端口为18090
目标平台域 | 云平台的Region，等于环境变量中的OS_REGION_NAME
存储可用区 | 云平台存储zone，默认nova，可以使用cinder service-list查看
用户 | 云平台登陆的用户名
密码 | 云平台登陆密码
目标云平台项目名称| 一般和用户名一致
目标云平台地址| 例http://192.168.10.201:5000/v3




**3. 配置向导完成**

密码修改完成后，重新登陆，确认配置信息无误后配置向导完成 

![45.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/10.png ':size=90%')
