

---

## 阿里云（公）
**1. 登录阿里云‘管理控制台’，点击【云服务器ECS】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/1.png ':size=80%')

**2. 点击【实例】→选择创建实例的地域→点击【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/2.png ':size=80%')

**3. 基础配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/3.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费方式  | 按量付费
地域  | 默认选择（与安全组地域一致）
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
实例规格/IPv6 | 默认不填
架构| X86计算
分类| 计算型C5（4U8G）
镜像| CentOS 7.5  64位
系统盘| 高效云盘 建议100G，最低40G

填写完成后点击【下一步，网络和安全组】，

**4. 网络和安全组配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/4.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
网络 | 选择创建安全组的同一VPC网络，任意可用交换机
公网带宽  | 勾选‘分配公网IPv4地址’，选择‘按使用流量’
带宽 | 选择‘5M’
安全组 | 选择开放12222/18090/3260/22端口号的安全组

选择完成后点击【下一步，系统配置】


**5. 系统配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/5.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
登录凭证 | 自定义密码
实例（主机）名称  | HyperGate

选择完成后点击【下一步，确认订单】。

**6. 确定订单：**

检查创建信息，勾选《云服务器ECS服务条款》，点击【创建实例】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/6.png ':size=80%')

**7. 创建成功：**

提示‘创建成功’，选择【管理控制台】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/7.png ':size=40%')


**8. 查看IP信息并记录：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/8.png ':size=80%')

---

## AWS

**1. 登录AWS‘管理控制台’，【服务】→【EC2】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/23.png ':size=80%')

**2. 点击【实例】→点击【启动实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/24.png ':size=80%')

**3. 选择AMI：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/25.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
操作系统  | centos7.3~7.5 64位（X86）



**4. 选择实例类型：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/26.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
系列 | 通用型
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB

选择完成后点击【下一步，配置实例】


**5. 配置实例：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/27.png ':size=80%')

选择网络VPC，完成后点击【下一步，添加存储】

**6. 添加存储：**


![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/28.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
存储大小 | 通用型SSD 建议100G，最低40G


**7. 添加标签：**


![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/29.png ':size=80%')

将实例命名为‘HyperGate’，完成后点击【下一步，配置安全组】

**8. 配置安全组：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/30.png ':size=80%')

选择放行了12222/18090/3260/22端口的安全组后点击【审核和启动】。

**9. 审核：检查创建信息，点击【启动】：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/31.png ':size=80%')

**10. 创建成功，下载密钥对文件，查看IP信息并记录：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/32.png ':size=80%')


---


## 华为云（公）

**1. 登录华为云‘管理控制台’，选择地域→【弹性服务器】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/9.png ':size=80%')

**2. 【弹性服务器】→【购买弹性云服务器】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/10.png ':size=80%')

**3. 基础配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/11.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费模式  | 按量付费
区域 | 默认选择（与安全组地域一致）
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
机型 | 计算型C3.xlarge.2（4U8G）
镜像| CentOS 7.5  64位
系统盘| 高IO 建议100G，最低40G）

填写完成后点击【下一步，网络配置】，

**4. 网络配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/12.png ':size=80%')

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

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/14.png ':size=80%')

确认完成后点击【立即购买】

**7. 创建成功：**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/15.png ':size=80%')


---



## 腾讯云（公）

**1. 登录腾讯云‘管理控制台’，点击【云服务器ECS】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/1.png ':size=80%')

**2. 点击【实例】→选择创建实例的地域→点击【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/2.png ':size=80%')

**3. 基础配置：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/3.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
计费方式  | 按量付费
地域  | 默认选择（与安全组地域一致）
vCPU  | 建议值: 4vCPU，最低2vCPU
内存 | 建议值: 8GiB，最低4GiB
实例规格/IPv6 | 默认不填
架构| X86计算
分类| 计算型C5（4U8G）
镜像| CentOS 7.5  64位
系统盘| 高效云盘 建议100G，最低40G

填写完成后点击【下一步，网络和安全组】，

**4. 网络和安全组配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/4.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
网络 | 选择创建安全组的同一VPC网络，任意可用交换机
公网带宽  | 勾选‘分配公网IPv4地址’，选择‘按使用流量’
带宽 | 选择‘5M’
安全组 | 选择开放12222/18090/3260/22端口号的安全组

选择完成后点击【下一步，系统配置】


**5. 系统配置：** 

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/5.png ':size=80%')

?>  配置内容填写参考：

字段  | 填写
------------- | -------------
登录凭证 | 自定义密码
实例（主机）名称  | HyperGate

选择完成后点击【下一步，确认订单】。

**6. 确定订单：**

检查创建信息，勾选《云服务器ECS服务条款》，点击【创建实例】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/6.png ':size=80%')

**7. 创建成功：**

提示‘创建成功’，选择【管理控制台】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/7.png ':size=50%')


**8. 查看IP信息并记录：**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/Appendix/8.png ':size=80%')

---