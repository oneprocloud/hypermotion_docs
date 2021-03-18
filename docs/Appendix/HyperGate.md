---


### 2.1 阿里云（公）

**1. 登录阿里云‘管理控制台’，点击【云服务器ECS】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/8.png ':size=100%')

**2. 点击【实例】→选择创建实例的地域→点击【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/9.png ':size=100%')

**3. 基础配置**

![10.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/10.png ':size=100%')

?> 创建实例基础配置参考以下内容

选项  | 选项填写
-----------------| -------------
计费方式   | 按量付费
地域 | 默认选择（与安全组地域一致）
vCPU | 建议值: 4vCPU，最低2vCPU
内存      | 建议值: 8GiB，最低4GiB
实例规格/ IPv6  | 默认不填
架构 | X86计算
分类  | 计算型C5（4U8G）
镜像 | 1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘 | 高效云盘 建议100G，最低40G

!> 注：如未上传镜像源，请参考文档中的导入自定义镜像上传自定义镜像，或联络我们的实施工程师获取共享镜像。

填写完成后点击【下一步，网络和安全组】，

**4. 网络和安全组配置**

![11.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/11.png ':size=100%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
网络   | 选择创建安全组的同一VPC网络，任意可用交换机
公网带宽| 勾选‘分配公网IPv4地址’，选择‘按使用流量’
带宽 | 选择‘5M’
安全组    | 选择开放12222/18090/3260/22端口号的安全组

选择完成后点击【下一步，系统配置】，

**5. 系统配置**

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/12.png" ':size=100%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
登录凭证| 自定义密码
实例名称| HyperGate
主机名 | HyperGate

选择完成后点击【下一步，确认订单】，

**6. 确认订单**

检查创建信息，勾选《云服务器ECS服务条款》，点击【创建实例】,

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/13.png" ':size=90%')

**7. 创建成功**

提示'创建成功'，选择【管理控制台】,

![14.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/14.png" ':size=45%')

**8. 查看IP信息并记录**

![15.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/15.png" ':size=90%')

---


### 2.2 AWS

**1. 登录AWS‘管理控制台’，【服务】→【EC2】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/1.png ':size=90%')

**2. 点击【实例】→点击【启动实例】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/2.png ':size=90%')

**3. 选择AMI：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/3.png ':size=90%')


?> 配置参考以下内容

选项  | 选项填写
-----------------| -------------
操作系统   | centos7.3~7.5 64位（X86）



**4. 选择实例类型**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/4.png ':size=90%')


?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
系列  | 通用型
vCPU| 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB


填写完成后点击【下一步，配置实例】，

**5. 配置实例**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/5.png ':size=90%')

选择网络VPC，完成后点击【下一步，添加存储】

**6. 添加存储**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/6.png ':size=90%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
存储大小  | 通用型SSD 建议100G，最低40G



**7. 添加标签**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/7.png ':size=90%')

将实例命名为‘HyperGate’，完成后点击【下一步，配置安全组】



**8. 配置安全组**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/8.png ':size=90%')

选择放行了12222/18090/3260/22端口的安全组后点击【审核和启动】

**9. 审核**

检查创建信息，点击【启动】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/9.png ':size=90%')

**10. 创建成功，下载密钥对文件，查看IP信息并记录：**


![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/10.png ':size=90%')

----

### 2.3 Azure

**1. 登录Azure‘管理控制台’，【虚拟机】→【添加】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/1.png ':size=90%')

**2. 选择操作系统**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/2.png ':size=90%')

?> 配置参考以下内容

选项  | 选项填写
-----------------| -------------
操作系统   | centos7.3~7.5 64位（X86）


**3. 配置实例信息：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/3.png ':size=90%')



**4. 配置用户密码和入站端口规则：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/4.png ':size=90%')


?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
用户名  | centos7.3~7.5 64位（X86）



**5. 选择磁盘类型：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/5.png ':size=90%')




**6. 选择网络：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/6.png ':size=90%')




**7. 确认配置信息：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/7.png ':size=90%')


检查创建信息，点击【创建】


**8. 创建成功，查看IP信息并记录：**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/8.png ':size=90%')

---

### 2.4 腾讯云（公）


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
镜像   |  1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
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

### 2.5 华为云（公）

**1. 登录华为云‘管理控制台’，选择地域→【弹性服务器】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/9.png ':size=90%')

**2. 【弹性服务器】→【购买弹性云服务器】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/10.png ':size=90%')

**3. 基础配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/11.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费模式  | 按量付费
区域 | 默认选择（与安全组地域一致）
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
机型 | 计算型C3.xlarge.2（4U8G）
镜像|  1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘| 高IO 建议100G，最低40G）

填写完成后点击【下一步，网络配置】，

**4. 网络配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/12.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
网络 | 选择创建安全组的同一VPC网络，任意可用交换机
安全组 | 选择开放12222/18090/3260/22端口号的安全组
弹性公网IP | 选择‘现在购买’
带宽类型| 选择‘独享带宽’
计算方法| 选择‘按使用流量’
带宽| 选择‘5M’

填写完成后点击【下一步，高级配置】，


**5. 高级配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/13.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
云服务器名称 | HyperGate
登陆凭证 | 根据实际需要选择


**6. 确认配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/14.png ':size=90%')

确认完成后点击【立即购买】

**7. 创建成功：**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/15.png ':size=90%')

---


### 2.6 金山云

**1. 登录金山云‘管理控制台’，【云服务器】→【实例】→选择地域→【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/1.png ':size=90%')

**2. 选择配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/2.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费模式  | 按小时配置实时付费
数据中心 | 默认选择（与安全组地域一致）
可用区  | 默认选择（与安全组地域一致）
云服务器类型 | 建议值: 4vCPU，最低2vCPU
CPU | 建议值: 8GiB，最低4GiB
内存|  建议值: 8GiB，最低4GiB
镜像| 1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘| SSD云盘 建议100G，最低40G


**3.选择弹性IP：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/3.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
绑定弹性IP  | 勾选‘购买新的弹性IP’
系统盘 | 高效云盘 建议100G，最低40G
公网带宽  | 勾选‘免费分配独立公网IP’，选择‘按使用流量’
带宽 | 选择‘5M’

其余默认，填写完成后点击【下一步】，

**4. 设置VPC：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/4.png ':size=90%')

选择网络VPC和开放了12222/18090/3260/22端口的安全组，点击【下一步】


**5. 设置基本信息** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/5.png ':size=90%')

选择完成后点击【购买】，


**6. 确认配置信息**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/6.png ':size=90%')

确认完成后点击【提交订单】

**7. 创建成功**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/7.png ':size=90%')

---

### 2.7 OpenStack

**1. 登录OpenSatck‘管理控制台’，点击【实例】→【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image007.png ':size=90%')

**2. 填写实例名称‘HyperGate’**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image008.png ':size=90%')


**3.选择名称为‘HM_IMG_<date>.qcow2’的镜像源**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image009.png ':size=90%')



**4. 选择实例配置** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image010.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
磁盘  | 建议100G，最低40G



**5. 选择网络** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image011.png ':size=90%')

**6. 选择安全组** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image012.png ':size=90%')


**7. 创建成功**

根据实际需求，可跳过非※创建项，点击‘创建实例’按钮创建实例，
完成后实例列表会显示创建实例，记录该实例的IP地址。

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/OpenStack/image013.png ':size=90%')

---

### 2.8 青云

**1. 登录青云‘管理控制台’，【主机】→【创建】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image007.png ':size=90%')

**2. 选择映像**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image008.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
映像版本 | CentOS 7.5 64位


**3.配置选择**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image009.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
可用区  | 与安全组地域一致
主机类型 | 基础型
CPU  | 建议值: 4vCPU，最低2vCPU
内存  | 建议值: 8GiB，最低4GiB
系统盘  | 建议100G，最低40G


**4. 网络设置** 

选择网络VPC，点击【下一步】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image010.png ':size=90%')




**5. 设置基本信息** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image011.png ':size=90%')

选择完成后点击【创建】，


**6. 创建成功**

在主机列表中查看创建信息，记录该主机的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image012.png ':size=90%')

**7. 添加防火墙规则**

选择开放了12222/18090/3260/22端口的防火墙，【更多操作】→【应用防火墙规则】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image013.png ':size=90%')

绑定HyperGate主机，点击【提交】按钮。

---


### 2.9 天翼云

**1. 登录天翼云‘控制中心’，【弹性云主机】→【创建弹性云主机】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image007.png ':size=90%')

**2. 选择配置**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image008.png ':size=90%')


?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费方式  | 按需计费
区域 | 默认选择（与安全组地域一致）
可用分区 |默认选择（与安全组地域一致）
CPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
镜像 | 公共镜像，CentOs7.3~7.5
系统盘 | 高IO 建议100G，最低40G



**3.网络配置**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image009.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
安全组  | 选择放行了端口12222/18090/3260/22的安全组
弹性IP | 勾选‘自动分配’
计费方式| 选择‘按流量计费’
带宽  | 选择‘5M’

填写完成后点击【下一步】，


**4. 高级配置** 


![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image010.png ':size=90%')


填写实例名称和密码后点击【下一步 确认配置】，


**5. 确认配置信息** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image011.png ':size=90%')


确认完成后点击【立即购买】。


**6. 创建成功**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image012.png ':size=90%')

---

### 2.10 UCloud

**1. 登录UCloud‘管理控制台’，【全部产品】→【云主机】→【创建主机】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image007.png ':size=90%')

**2. 基础配置**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image008.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
地域  | 默认选择（与安全组地域一致）
配置方式 | 自定义配置
镜像 |默认选择（与安全组地域一致）
CPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
磁盘 | 1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
网络 | 选择创建安全组的同一VPC网络及子网



**3.网络配置**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image009.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费方式  | 选择‘流量计费’
带宽 | 选择‘5M’
防火墙| 选择放行端口12222/18090/3260/22
主机名称  | HyperGate

填写完成后点击【立即购买】

**4. 确认配置信息** 


![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image010.png  ':size=90%')

确认完成后后点击【立即支付】，




**5. 创建成功**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image011.png  ':size=90%')

---

### 2.11 ZStack

**1.登录ZStack‘管理控制台’，点击【云资源池】→【云主机】→【创建云主机】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ZStack/image007.png ':size=90%')

**2. 填写实例名称‘HyperGate’**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ZStack/image008.png ':size=90%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
名称  | HyperGate
计算机规格 | 建议值: 4U8G，最低2U4G
镜像 |1.**SaaS版**：选择公共镜像，CentOS 7.5  64位；</br>2.**单机版**：选择自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）



**3.选择网络**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ZStack/image009.png ':size=90%')



**4. 选择亲和组** 


![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ZStack/image010.png  ':size=90%')





**5. 创建成功**

根据实际需求，可跳过非必选创建项， 创建成功后可在云主机列表中查看该主机并记录该云主机例的IP地址。

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ZStack/image011.png  ':size=90%')





