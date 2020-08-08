### 服务健康检查

1. 登陆后，系统自动跳转至【配置向导】服务健康检查界面，自动检测服务健康状况，确认服务健康状况均正常，点击【下一步】

![28.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/28.png ':size=80%')

 ---
### 激活License

- 阅读激活说明，确认后根据实际需要在以下两种方式中任选一种进行激活：

![29.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/29.png ':size=80%')

#### 方式一：扫描二维码（推荐）

1. 使用手机上的“微信”、“钉钉”、“支付宝”或带有扫描二维码的“浏览器”，扫描对话框中的二维码，并按要求填写相关信息

![31.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/31.png ':size=80%')

!> *注：请正确填写公司名称、姓名、职位等信息，否则将无法收到序列号信息。                           

2. 扫描二维码方式提交成功后，激活码将以附件形式发送至所填写的邮箱中，请注意查收。收到激活码后粘贴到“激活码”框中，点击【激活】。

#### 方式二：发送邮件

1. 点击【点击复制注册码】，将注册码以邮件形式发送至license@oneprocloud.com

![30.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/30.png ':size=80%')

!> 注：请正确填写公司名称、姓名、职位等信息，否则将无法收到序列号信息。                           

2. 邮件方式提交成功后，激活码将以附件形式发送至所填写的邮箱中，请注意查收，收到激活码后粘贴到“激活码”框中，点击【激活】

![32.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/32.png ':size=80%')

3. 确认信息无误后点击【下一步】

---
### 源端连接设置

!> 请根据实际需求选择源端待迁移主机迁移方式，目前支持**「Agent代理」**及**「Agentless无代理」**两种模式

#### 无代理方式 - 连接VMware平台

1. 选择VMware图标，自动跳转下一步

![33.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/33.png ':size=80%')

2. 填写vCenter相关信息后选择【下一步】

![34.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/34.png ':size=80%')

?> 需要填写源端VMware链接信息说明如下所示

字段  | 含义
------------- | -------------
vCenter IP 地址   | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码

3. 系统提示’创建源端连接成功’，点击下一步

![35.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/35.png ':size=80%')

#### 无代理方式 - 连接OpenStack平台

1. 选择OpenStack图标，自动跳转下一步

![36.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/36.png ':size=80%')

2. 填写OpenStack源平台信息后选择【下一步】

![37.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/37.png ':size=80%')

?> 需要填写源端OpenStack+Ceph链接认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
-----------------| -------------
云平台地址&nbsp; &nbsp; &nbsp; &nbsp;    | 例：http://192.168.11.201:5000/v3/
云平台域  | region（例：RegionOne、RG1、RG2）
租户组  | 项目组域名（默认为default）
云平台租户      | 租户、或项目名称、一般为登陆云平台的用户名(例：admin、xiaoming)
用户组  | 用户组域名 (默认为default)
云平台用户  | 登陆云平台的用户名
用户密码  | 登陆云平台的密码

3. 填写Ceph信息后选择【下一步】

![38.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/38.png ':size=80%')

?> 需要填写源端Ceph链接认证信息说明如下所示

字段 | 含义
-----------------| -------------
Ceph控制节点地址&nbsp; &nbsp; &nbsp; &nbsp;   | ceph控制节点的地址  （例如：10.0.0.201） 需确认双方可以网络互通
Ceph集群 | 目前仅支持ceph
Ceph存储池  | ceph节点的存储池名称，默认为volumes
Ceph用户名     |ceph的用户名（例如：cinder、admin）
Ceph密匙环 | ceph的键值，在ceph控制节点cat /etc/ceph/ceph.client.admin.keyring查看

4. 系统提示’创建源端连接成功’，点击下一步

#### 代理方式 - 连接windows主机

1. 选择物理机机X86图标，自动跳转下一步

![39.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/39.png ':size=80%')

3. 点击选择所要获取的Agent安装包，进行下载

![40.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/40.png ':size=80%')

4. 在待迁移物理机上安装Agent

!> 注：物理机端安装操作步骤可参考 附录一Windows Agent安装说明

?> 所有对Agent的操作均在HyperMotion端触发，Windows Agent服务正常启动后，可在HyperMotion中看到注册的主机。

#### 代理方式 - 连接Linux主机

1. 选择所要迁移Linux主机图标，自动跳转下一步

![41.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/41.png ':size=80%')

2. 点击选择所要获取的Agent安装包，进行下载

![42.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/42.png ':size=80%')

3. 在待迁移Linux主机上安装Agent

!> 注：Liunx主机端安装操作步骤可参考 附录二 Linux  Agent安装说明

?> 所有对Agent的操作均在HyperMotion端触发，linux  Agent服务正常启动后，可在HyperMotion中看到注册的主机。

---