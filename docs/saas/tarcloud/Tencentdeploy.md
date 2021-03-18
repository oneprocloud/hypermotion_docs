

---
## 1. 创建实例，命名为 HyperGate

**1. 登录腾讯云‘管理控制台’，【实例】→选择地域→【新建】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/1.png ':size=90%')

**2. 选择机型1：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/2.png ':size=90%')

?> 配置信息填写参考以下内容

选项  | 选项填写
-----------------| -------------
配置方式   | 自定义配置
计费方式 | 按量付费
地域 | 默认选择（与安全组地域一致）
网络      | 选择创建安全组的同一VPC网络及子网
vCPU    | 建议值: 4vCPU，最低2vCPU
内存      | 建议值: 8GiB，最低4GiB
机型     | 计算型C3（4U8G）


**3. 选择机型2-选择镜像：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/3.png ':size=90%')

?> 配置信息填写参考以下内容

选项  | 选项填写
-----------------| -------------
镜像   | 自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘 | 高效云盘 建议100G，最低50G
公网带宽 | 勾选‘免费分配独立公网IP’，选择‘按使用流量’
带宽      | 选择‘5M’

!> 注：如未上传镜像源，请参考文档中的导入自定义镜像上传自定义镜像，或联络我们的实施工程师获取共享镜像。

填写完成后点击【下一步，设置主机】，

**4. 设置主机1-选择安全组：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/4.png ':size=90%')


**5. 设置主机1-主机名和密码**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/5.png ':size=90%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
实例名称| HyperGate
登陆方式| 按需求选择，此处勾选‘保留镜像设置’

选择完成后点击【下一步，确认配置信息】

**6. 确认配置信息**


![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/6.png ':size=90%')

确认完成后点击【开通】

**7. 创建成功**

在实例列表中查看创建信息，记录该实例的IP地址

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/7.png ':size=90%')



---

## 2. 打开实例控制台

**1. 在实例列表中，点击创建实例的【远程连接】按钮， **

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/8.png ':size=90%')

---

## 3. 自动进入安装部署界面

**1. 登录后自动进入安装界面，光标选择到'HyperGate'，'Enter'键入**

![19.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/19.png" ':size=70%')

**2. 系统自动部署完成**

![20.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/20.png" ':size=70%')

---

## 4. 上传HyperDoor镜像

**1. 获取HyerDoor镜像;**

**2. 管理控制台界面，选择【云服务器ECS】-【实例】**

**3. 在实例列表中，点击创建实例的【更多】-【磁盘和镜像】-【创建自定义镜像】**

![21.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/21.png" ':size=90%')

**4. 填写自定义镜像名称、自定义镜像描述，默认资源组，并选择【创建】**

![22.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/22.png" ':size=60%')

**5. 管理控制台页面，选择【云服务器ECS】-【镜像】，记录该镜像ID**

![23.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/23.png" ':size=90%')
