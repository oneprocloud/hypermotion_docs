# 迁移操作使用手册
## 登陆访问

!> 支持以下浏览器：Chrome(谷歌)，Firefox（火狐），Safari

?> 访问地址：http://< HyperMotion IP>:18088

![27.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/27.png ':size=80%')

```
用户名：admin
初始密码：admin_pass
```

!> 1. HyperMotion IP即创建HyperMotion虚机时的IP</br>
2. http://<HyperMotion IP>:18088中的":"为英文格式

## 配置向导

[confwiz.md](../confwiz.md ':include')

### 阿里云连接设置

1. 配置向导进入‘目标端平台配置’界面，选择阿里云图标

![43.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/43.png ':size=80%')

2. 填写云平台认证信息后点击【下一步】

![44.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/44.png ':size=80%')

?> 需要填写目标云端认证信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与阿里云互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录二 阿里云平台认证信息获取)
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录二 阿里云平台认证信息获取)
API接入地址 | 默认 ecs.aliyuncs.com

?> 需要填写相关地域、可用区以及镜像ID信息说明如下，请按照需求进行查找并填写

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：华北、华东、香港）
可用区ID  | 选择安装HyperGate虚机所在区域 （如华北1可用区B  华北1 可用区C）
镜像ID | 创建的阿里云的镜像ID（详情参见附录二 阿里云平台认证信息获取）

---
### 配置向导完成

1. 目标平台配置信息填写完成后，点击【下一步】，确认配置信息无误后配置向导完成，系统提示修改密码后重新登录

![45.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/45.png ':size=80%')
## 迁移向导

返回概览界面，点击迁移向导中的‘选择主机’步骤，进入迁移向导界面

![46.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/46.png ':size=80%')

### 选择待迁移主机

1. 进入迁移向导界面后，选择【添加主机】

![48.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/48.png ':size=80%')

2. 选择【源端类型】，选择‘VMware’

![49.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/49.png ':size=80%')

3. 列表中自动列出vCenter平台连接下的全部虚拟机，勾选需迁移的虚机后，点击【确认】

![50.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/50.png ':size=80%')

4. 系统跳转回‘选择主机’界面，选择添加的待迁移虚机，点击下一步

![51.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/51.png ':size=80%')

---

### 数据拷贝
1. 选择已经设定的一个存储设备连接，点击【确定】

![52.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/52.png ':size=80%')

2. 同步数据，完成后点击【下一步】

![53.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/53.png ':size=80%')

3. 在跳出“同步数据”对话框中点击【确定】

![54.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/54.png ':size=80%')

?> 安装Agent的主机可设定同步速率

![55.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/55.png ':size=80%')

4. 等待数据同步完成，完成继续点击下一步

![56.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/56.png ':size=80%')

---

### 开始迁移并完成迁移

1. 选择待迁移主机，点击启动主机

![57.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/57.png ':size=80%')

2. 系统自动跳出提示框，选择确认无误后点击【确定】

![58.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/58.png ':size=80%')

3. 系统提示‘开始启动主机’，等待启动主机，系统提示‘启动系统完成’

![59.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/59.png ':size=80%')

4. 登陆目标平台重启迁移主机后登陆并检查系统及应用完整性。

!> *注：待迁移主机将在目标平台上创建。请到HyperGate所在租户查看资源*

### 清理迁移资源

*请根据以下步骤提示清理：*

1. 选择已迁移完成的主机，点击【资源清理】

![60.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/60.png ':size=80%')

2. 系统自动弹出‘资源清理’，勾选‘强制清理’，点击【确定】

![61.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/61.png ':size=80%')

3. 清理成功后，可在【已清理】界面查看已迁主机的具体地址。