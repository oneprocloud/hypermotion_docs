---

## 1 创建HyperGate实例（目标平台操作）

### 1.1 阿里云

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


### 1.2 AWS
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

### 1.3 Azure

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

### 1.4 腾讯云


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

### 1.5 华为云

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


### 1.6 金山云

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

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/5.png ':size=80%')

选择完成后点击【购买】，


**6. 确认配置信息**

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/6.png ':size=90%')

确认完成后点击【提交订单】

**7. 创建成功**

在实例列表中查看创建信息，记录该实例的IP地址

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/7.png ':size=90%')

---

### 1.7 OpenStack



### 1.8 青云

### 1.9 天翼云

### 1.10 UCloud

### 1.11 ZStack

---

## 2 Agent安装说明（源机操作）


### 2.1 Windows Agent安装说明


**1. 登录Windows主机并安装可执行文件（源端本地）**


!> 注：除Windows 2003 x86版本默认安装路径不同，其他版本安装过程无差异。</br>

?> 用户须在管理员模式下安装**Windows-Agent-Installer.exe文件**。</br>


打开安装界面，如下图（默认安装路径为“C:\Program Files\Windows-Agent”）点击【下一步】，按引导步骤安装

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image043.png ':size=40%') &ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image044.png ':size=40%')

!> 注：安装过程中，不同的安装包会根据不同的系统安装依赖程序，Windows 2008以下的版本没有自带Microsoft Initiator程序，会同其他依赖程序一并进行安装。</br>


![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image045.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image046.png ':size=40%')

安装完成后，点击【完成】，并根据提示重启主机.

!>注：1. 安装完成后，会在所选安装目录的同级目录生成一个“Windows-Agent”文件夹，此文件夹为程序运行目录，运行生成的相关日志也保存在此文件夹中;</br>
 &ensp;&ensp;&ensp; 2. 安装完成后，需重启主机已保障Windows agent的正常运行。



**2. 初始化ISCSI服务（源端本地）**

【控制面板】→【系统和安全】→【管理工具】→运行iSCSI Initiator程序

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image047.png ':size=60%')


**3. 配置防火墙（源端本地）**


?>请根据实际需要在以下两种环境中选择配置：</br>

	Windows 2008/2012/2016
打开【Windows防火墙】，将Windows-Agent.exe服务加入防火墙允许服务，根据版本不同，设置方式略有差异，详见下图所示：

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image048.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image049.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image050.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image051.png ':size=40%')

注：默认路径：C:\Users\Administrator\AppData\Local\Microsoft\Windows

	Windows 2003
打开Windows防火墙，依次点击【例外】→【添加程序】→【浏览】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image052.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image053.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image054.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image055.png ':size=40%')

选中Windows-Agent.exe程序，点击【打开】；
在“添加程序”列表可看到“Windows-Agent.exe”默认被选中，点击【确定】完成添加，并重启系统。

注：1. 非app.exe程序;
2. 目录默认为“C:\Program Files (x86)\Windows-Agent\ Windows-Agent.exe”，
2003 X86为“C:\Program Files\ Windows-Agent\ Windows-Agent.exe



**4. 运行程序（源端本地）**

安装、配置防火墙并重启后，点击桌面【Windows-agent】将其运行；

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image056.png ':size=10%')

?> 按以下格式要求填写：</br>
&ensp;&ensp;&ensp;HyperMotion访问地址：http://:HyperMotionIP:18766。
&ensp;&ensp;&ensp;NAT地址：填写本地NAT地址（纯IP地址），若为空，则会默认使用本机IP作为参数，点击【启动】；

### 2.2 Linux Agent安装说明

---

## 3  云平台认证信息获取（目标平台操作）



---

## 4  限制信息-安装或操作前须知

### 4.1	网络带宽建议
迁移过程中主要通过网络进行数据拷贝，所以推荐的网络速度如下：
1) **全量数据同步**，建议最小带宽10Mbps
2) **增量数据同步**，建议最小带宽1Mbps


### 4.2	源平台限制信息

**1.	Linux物理机**</br>
	文件系统仅支持ext2, ext3，ext4，xfs，ntfs，目前暂时不支持btrfs(SUSE 12默认的安装系统)；</br>
	挂载文件系统的分区的需要预留10%的空间，例如：root分区的大小为100G，则剩余空间需要在10G以上；</br>
	不支持没有挂载文件系统的分区同步；</br>
	不支持没有划分分区的磁盘同步；</br>
	不支持多路径磁盘同步（受不同厂商多路径软件的局限）；</br>
	不支持复杂的LVM结构（仅支持单个VG的情况）；</br>
	不支持裸设备同步；</br>
	安装Linux Agent时需要yum clean all，旧的yum源信息可能会造成HyperGate无法安装。</br>

---
### 4.3. 目标平台限制信息

**4.3.3 阿里云**

- 首次迁移上云后，默认将该实例镜像用按量付费的形式创建，验证后可删除该实例，手动将该镜像创建实例，改为包月形式;</br>
- 阿里云目前最小支持20G的盘，如果源端有小于20G的盘，上云后默认扩大为20G的盘;</br>
- 迁移时，源主机磁盘个数不能大于18个盘;</br>
- 阿里云平台的目标云平台服务只能挂载16个盘，需要手动调整 (将目前20个卷设定改为16个卷受设定)；源主机磁盘个数不能大于16个盘;</br>
- 由于目前阿里云系统盘最大为500 GB，所以待迁移的主机的系统盘不能大于500 GB，根据阿里云官方提供的方法，在大于500G的情况下，需手动的对源系统进行缩容。

---
**4.3.3 AWS**

- 目前只支持CentOS6/Centos7版本的迁移；</br>
- 支持RHEL/CentOS 6.x & 7.x版本迁移；</br>
- 迁移RHEL/CentOS 6.x & 7.x前需要将源系统内部防火墙关闭或开放22端口，否则迁移后无法远程连接；</br>
- 迁移Windows版本前需要将源系统内部防火墙关闭或开放远程桌面3389端口，否则迁移后无法远程连接；</br>
- 迁移到AWS时支持创建卷格式为gp2；</br>
- 在AWS创建HyperGate时建议使用 "社区AMI CentOS" 以下版本镜像；</br>
- Linux HyperDoor创建流程：HyperGate安装完成后 --> 关机，使用HyperGate实例生成Linux HyperDoor镜像；</br>
- 建议使用以下版本镜像为基础制作Windows HyperDoor镜像；</br>
- 不支持源端 "OpenStack+Ceph (Agentless)" 迁移至AWS；</br>
- 迁移后主机所在的 "域、可用区、VPC、子网、安全组" 皆需与HyperGate一致；</br>
- 仅支持T3系列的实例类型，T3限制挂盘最多28个、网口至少占用1个、实例根卷用1个；极限条件下，T3系的实例最多能附加3个网口，HyperGate最多仅能同时挂载20个卷 (迁移用)；</br>
- 目标云平台服务最大同时挂载卷 (磁盘) 个数为：20个。</br>

---
**4.3.3 Azure**

- 实例磁盘限制最大容量为: 32TB；
- 由于Azure临时存储盘的关系，HyperGate数据盘会由第三块盘开始挂载 (第一块盘: 系统盘，第二块盘: 临时存储盘)；</br>
- 由于Azure临时存储盘的关系，Windows主机迁移后需登入系统将数据盘手动启动 (Activate)，并指定盘符 (若Windows系统没有自动给予盘符)；</br>
- Azure目前仅支持Windows 2008 SP2及以上版本的实例类型；HyperMotion迁移支持Windows 2008 R2及以上版本和RHEL/CentOS 6 & 7版本操作系统，包含驱动修复功能 (磁盘及网络自动获取修复) (Windows 2008 SP2不支持手动或自动驱动修复)；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：16个 (HyperGate实例类型: F4)。</br>

---

**4.3.3 腾讯云**

- 迁移上云后，默认使用按量付费形式创建实例，验证后可手动改为包月或其他形式；</br>
- 迁移使用的HyperDoor为内存OS系统，启动实例时内存最小需求为2GB；</br>
- 驱动修复时需要进行系统盘全量数据拷贝，启动实例耗费时间较长；</br>
- HyperDoor方式实例启动时会较长时间占用HyperGate Worker数，建议HyperGate使用CPU个数较高的配置 (目前worker数等于CPU个数)，建议8-Core或以上；</br>
- 目前不支持在启动实例时选择Region和Zone，即所有迁移上云的实例都需和HyperGate处于相同区域；</br>
- 启动实例不支持安全组选择，默认需和HyperGate相同；</br>
- 腾讯云系统盘最小支持50GB最大支持1TB (SSD类型最大支持500GB)；</br>
- 腾讯云数据盘根据类型不同支持最小容量10GB和最大容量16000GB，且磁盘容量为10GB的整数倍；</br>
- 迁移时，源主机磁盘个数最多支持20个盘；</br>
- Windows 2016主机在迁移后配置DHCP方式获取不到IP地址，需要人为介入；</br>
- Windows 2003主机在迁移后驱动修复有无法成功的几率发生 (会进入HyperDoor画面而不是正常操作系统画面)，解决方式可尝试重新启动实例；</br>
- Linux主机在迁移后会使用DHCP服务分配动态主机名，导致原静态主机名失效；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：20个。</br>

**4.3.3 华为云**

- 此版本针对Windows 2003操作系统迁移不支持网卡驱动修复；</br>
- Windows 2012 / R2、Windows 2016操作系统迁移网卡驱动需要待实例启动成功后手动安装；</br>
- 迁移后主机所在的 "域、可用区、VPC、子网、安全组" 皆需与目标云平台服务一致；</br>
- 华为公有云实例支持：系统盘最小容量40GB、最大1TB， 数据盘最小容量10GB、最大32TB；如果源主机系统和数据磁盘不足40GB或10GB，默认会以支持最小值创建；</br>
- 目标云平台服务最大同时挂载卷 (磁盘) 个数为：23个。</br>


**4.3.3 金山云**
- 迁移到金山公有云的系统如果启动失败那么需要重新同步数据；</br>
- 迁移系统的系统盘大小只能小于等于20GB。</br>

**4.3.3 OpenStack**

- 迁移使用的HyperDoor为内存OS系统，启动实例时内存最小需求为2GB；</br>
- 驱动修复时需要进行系统盘全量数据拷贝，启动实例耗费时间较长；</br>
- 如驱动修复程序于HyperDoor进行，不会占用同步时HyperGate可用同时挂载卷数量；</br>
- 启动实例不支持安全组选择，默认需和HyperGate相同；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：20个。</br>


**4.3.3 青云**

- 迁移使用的HyperDoor为内存OS系统，启动实例时内存最小需求为2GB。</br>
- 驱动修复时需要进行系统盘全量数据拷贝，启动实例耗费时间较长；</br>
- 由于驱动修复程序于HyperDoor进行，并不会占用同步时HyperGate可用同时挂载卷数量；</br>
- 启动实例不支持安全组选择，默认需和HyperGate相同；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：20个。</br>

**4.3.3 UCloud**

- 安装建议选择通用型N主机；</br>
- 最大挂载volume数目：建议不超过5个。</br>

**4.3.3 UCloud**

- 在迁移过程中，由于ZStack平台暂无法获取虚拟机内部磁盘信息，因此不能重启HyperGate，否则将导致迁移失败；
- 目前只支持管理员账户进行鉴权，不支持其他方式，例：LDAP、项目登陆等；
- 仅支持使用管理员权限的用户操作HyperMotion：在创建卷的过程中，需要创建卷规格，该操作权限目前只能支持管理员用户 (ZStack限制)；
- 若迁移主机包含多块磁盘，迁移后所有磁盘必须存在同一个存储资源池内；
- ZStack暂无提供根据卷ID对应盘符的方法 (virtio驱动)，通过对比磁盘差异的方式适配；所以磁盘挂载后不支持手动卸载，必须由前端触发清理资源 (如果手动卸载后，会导致HyperGate无法启动主机)；
- ZStack镜像为独立副本，迁移后启动主机需要较长时间；
- 在ZStack上不支持将HyperGate布署于Centos 7.1 & 7.2上，会出现找不到磁盘路径的问题； 
- ZStack不支持Boot from Volume方式启动虚拟机，需将卷转为镜像后通过指定镜像服务器UUID实现启动主机流程；
- 如果镜像服务器UUID填写错误并不会阻碍流程，但是会影响主机启动，需要修改HyperGate Cloud Info文件；
- 迁移过程中，HyperGate不能进行重启；由于目前无法从虚拟机内部获取磁盘信息和云平台块设备进行关系对应，重启会导致磁盘顺序乱序；
- 由于ZStack平台对每台虚拟机挂载的盘最大不允许超过24个，所以在迁移至ZStack平台时，HyperGate最大挂载盘限制在15个 (剩馀可挂磁盘数保留给HyperGate系统盘及驱动修复用)。
