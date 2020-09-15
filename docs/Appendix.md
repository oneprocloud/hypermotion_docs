

---
## 限制信息-安装或操作前须知

### 1.	网络带宽建议
迁移过程中主要通过网络进行数据拷贝，所以推荐的网络速度如下：
1) **全量数据同步**，建议最小带宽10Mbps
2) **增量数据同步**，建议最小带宽1Mbps


### 2.	源平台限制信息

**1.	Linux物理机**</br>
	文件系统仅支持ext2, ext3，ext4，xfs，ntfs，目前暂时不支持btrfs(SUSE 12默认的安装系统)；</br>
	挂载文件系统的分区的需要预留10%的空间，例如：root分区的大小为100G，则剩余空间需要在10G以上；</br>
	不支持没有挂载文件系统的分区同步；</br>
	不支持没有划分分区的磁盘同步；</br>
	不支持多路径磁盘同步（受不同厂商多路径软件的局限）；</br>
	不支持复杂的LVM结构（仅支持单个VG的情况）；</br>
	不支持裸设备同步；</br>
	安装Linux Agent时需要yum clean all，旧的yum源信息可能会造成HyperGate无法安装。</br>

### 3.	目标平台限制信息

#### 阿里云

#### AWS



---
## 创建HyperGate实例（目标平台操作）

#### 阿里云

**1. 登录阿里云‘管理控制台’，点击【云服务器ECS】**

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/8.png ':size=90%')

**2. 点击【实例】→选择创建实例的地域→点击【创建实例】**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/9.png ':size=90%')

**3. 基础配置**

![10.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/10.png ':size=90%')

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
镜像 | 自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘 | 高效云盘 建议100G，最低40G

!> 注：如未上传镜像源，请参考文档中的导入自定义镜像上传自定义镜像，或联络我们的实施工程师获取共享镜像。

填写完成后点击【下一步，网络和安全组】，

**4. 网络和安全组配置**

![11.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/11.png ':size=90%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
网络   | 选择创建安全组的同一VPC网络，任意可用交换机
公网带宽| 勾选‘分配公网IPv4地址’，选择‘按使用流量’
带宽 | 选择‘5M’
安全组    | 选择开放12222/18090/3260/22端口号的安全组

选择完成后点击【下一步，系统配置】，

**5. 系统配置**

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/12.png" ':size=90%')

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

#### AWS
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

#### Azure

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


#### 腾讯云


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
## 云平台认证信息获取（目标平台操作）
---
## 自定义权限管理策略（目标平台操作）
---
## Agent安装说明（源机操作）
---
