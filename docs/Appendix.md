---

## 1  限制信息-安装或操作前须知


### 1.1	网络带宽建议
迁移过程中主要通过网络进行数据拷贝，所以推荐的网络速度如下：
1) **全量数据同步**，建议最小带宽10Mbps
2) **增量数据同步**，建议最小带宽1Mbps


### 1.2	源平台限制信息

**1.	Linux物理机**</br>
- 文件系统仅支持ext2, ext3，ext4，xfs，ntfs，目前暂时不支持btrfs(SUSE 12默认的安装系统)；</br>
- 挂载文件系统的分区的需要预留10%的空间，例如：root分区的大小为100G，则剩余空间需要在10G以上；</br>
- 不支持没有挂载文件系统的分区同步；</br>
- 不支持没有划分分区的磁盘同步；</br>
- 不支持多路径磁盘同步（受不同厂商多路径软件的局限）；</br>
- 不支持复杂的LVM结构（仅支持单个VG的情况）；</br>
- 不支持裸设备同步；</br>
- 安装Linux Agent时需要yum clean all，旧的yum源信息可能会造成HyperGate无法安装。</br>

**2.    VMware版本约束条件**</br>

虚拟化 | 版本   |   环境
------------- | ----------------------| ----------------------
VMware  |ESXi/vCenter/VMFS≥5.0 |虚拟机磁盘格式不可为RDM（RawDiskMapping）格式
  |   | 仅支持VMFS磁盘，虚拟机磁盘； </br>支持格式：FlatVer1, FlatVer2, SparseVer1, SparseVer2；</br>虚拟机版本: ≥7；</br> VMFS<5.5时：单磁盘容量必须<2032GB。
 |  |虚拟机支持Change Block Tracking
 |   |虚拟机磁盘模式必须为persistent
 |EXSi6.0|必须安装VMware ESXi 6.0 Build 2715440，
 
**3.    热迁移约束条件**</br>

- 虚拟机磁盘格式不可为RDM（RawDiskMapping）格式；</br>
- 仅支持VMFS磁盘，虚拟机磁盘支持格式：FlatVer1, FlatVer2, SparseVer1, SparseVer2；</br>
- 虚拟机版本: ≥7；</br>
- VMFS<5.5时：单磁盘容量必须<2032GB；</br>
- 不支持虚拟机中含有通过iSCSI方式共享磁盘的虚拟机。</br>

**4.    其他限制条件**</br>

- 在使用该工具前，为避免产生影响，建议停用一切VMware备份软件。例：Veeam、爱数等。</br>
- HyperMotion理论上不会对业务造成影响，但实际操作中，以下情况可能会出现快照过程中业务短时中断：</br>
(1). 虚拟机正在使用的磁盘有损坏；</br>
(2). 迁移中，用户手动对快照进行操作--【建议：不要手动对快照进行操作】；</br>
(3). 业务系统I/O过大，导致磁盘长时间处于100%利用率--【建议：在非
忙时执行数据拷贝】；</br>
(4). 用户待迁移的主机长时间没有重启或者有非常旧的快照（半年以上）--【建议：用户对系统进行关机，并手动触发一次快照后再执行迁移】。</br>

---
### 1.3. 目标平台限制信息


#### 1.3.1 阿里云（公）

- 首次迁移上云后，默认将该实例镜像用按量付费的形式创建，验证后可删除该实例，手动将该镜像创建实例，改为包月形式;</br>
- 阿里云目前最小支持20G的盘，如果源端有小于20G的盘，上云后默认扩大为20G的盘;</br>
- 迁移时，源主机磁盘个数不能大于18个盘;</br>
- 阿里云平台的目标云平台服务只能挂载16个盘，需要手动调整 (将目前20个卷设定改为16个卷受设定)；源主机磁盘个数不能大于16个盘;</br>
- 由于目前阿里云系统盘最大为500 GB，所以待迁移的主机的系统盘不能大于500 GB，根据阿里云官方提供的方法，在大于500G的情况下，需手动的对源系统进行缩容。

---
#### 1.3.2 AWS


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

#### 1.3.3 Azure

- 实例磁盘限制最大容量为: 32TB；
- 由于Azure临时存储盘的关系，HyperGate数据盘会由第三块盘开始挂载 (第一块盘: 系统盘，第二块盘: 临时存储盘)；</br>
- 由于Azure临时存储盘的关系，Windows主机迁移后需登入系统将数据盘手动启动 (Activate)，并指定盘符 (若Windows系统没有自动给予盘符)；</br>
- Azure目前仅支持Windows 2008 SP2及以上版本的实例类型；HyperMotion迁移支持Windows 2008 R2及以上版本和RHEL/CentOS 6 & 7版本操作系统，包含驱动修复功能 (磁盘及网络自动获取修复) (Windows 2008 SP2不支持手动或自动驱动修复)；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：16个 (HyperGate实例类型: F4)。</br>

---
#### 1.3.4 腾讯云（公）

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

---

#### 1.3.5 华为云（公）

- 此版本针对Windows 2003操作系统迁移不支持网卡驱动修复；</br>
- Windows 2012 / R2、Windows 2016操作系统迁移网卡驱动需要待实例启动成功后手动安装；</br>
- 迁移后主机所在的 "域、可用区、VPC、子网、安全组" 皆需与目标云平台服务一致；</br>
- 华为公有云实例支持：系统盘最小容量40GB、最大1TB， 数据盘最小容量10GB、最大32TB；如果源主机系统和数据磁盘不足40GB或10GB，默认会以支持最小值创建；</br>
- 目标云平台服务最大同时挂载卷 (磁盘) 个数为：23个。</br>

---

#### 1.3.6 金山云

- 迁移到金山公有云的系统如果启动失败那么需要重新同步数据；</br>
- 迁移系统的系统盘大小只能小于等于20GB。</br>

---
#### 1.3.7 OpenStack


- 迁移使用的HyperDoor为内存OS系统，启动实例时内存最小需求为2GB；</br>
- 驱动修复时需要进行系统盘全量数据拷贝，启动实例耗费时间较长；</br>
- 如驱动修复程序于HyperDoor进行，不会占用同步时HyperGate可用同时挂载卷数量；</br>
- 启动实例不支持安全组选择，默认需和HyperGate相同；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：20个。</br>

---

#### 1.3.8 青云



- 迁移使用的HyperDoor为内存OS系统，启动实例时内存最小需求为2GB。</br>
- 驱动修复时需要进行系统盘全量数据拷贝，启动实例耗费时间较长；</br>
- 由于驱动修复程序于HyperDoor进行，并不会占用同步时HyperGate可用同时挂载卷数量；</br>
- 启动实例不支持安全组选择，默认需和HyperGate相同；</br>
- HyperGate最大同时挂载卷 (磁盘) 个数为：20个。</br>

---

#### 1.3.9 UCloud


- 安装建议选择通用型N主机；</br>
- 最大挂载volume数目：建议不超过5个。</br>
---

#### 1.3.10 ZStack


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

---
#### 1.3.11 Ceph存储需求

如果使用的后端存储为Ceph，建议使用链式快照作为默认方式，这样在验
证过程时会加快启动速度，在迁移完成后可以将该种方式修改回非链式。</br>（使
用链式快照在资源清理时会遇到快照依赖关系的问题，需要使用flattern命
令进行断链操作。）

```
/etc/cinder/cinder.conf
[ceph]   rbd_flatten_volume_from_snapshot = False
```

---

#### 1.3.12 网络需求

- HyperMotion与HyperGate之间能通过IP地址互相访问；
- HyperGate可以访问云平台 API网络，并且能够正常调用云平台 API接口。

---

## 2 创建HyperGate实例（目标平台操作）

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

---

## 3 Agent安装说明（源机操作）


### 3.1 Windows Agent安装说明


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

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image047.png ':size=50%')


**3. 配置防火墙（源端本地）**


?>请根据实际需要在以下两种环境中选择配置：</br>


**<font face="中易宋体" size=4 color=blue>&ensp; • Windows 2008/2012/2016</font>**

打开【Windows防火墙】，将Windows-Agent.exe服务加入防火墙允许服务，根据版本不同，设置方式略有差异，详见下图所示：

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image048.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image049.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image050.png ':size=38%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image051.png ':size=45%')

!>注：默认路径：C:\Users\Administrator\AppData\Local\Microsoft\Windows

**<font face="中易宋体" size=4 color=blue>&ensp; • Windows 2003</font>**

打开Windows防火墙，依次点击【例外】→【添加程序】→【浏览】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image052.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image053.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image054.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image055.png ':size=40%')

选中Windows-Agent.exe程序，点击【打开】；
在“添加程序”列表可看到“Windows-Agent.exe”默认被选中，点击【确定】完成添加，并重启系统。

!>注：1. 非app.exe程序;</br>
  &ensp;&ensp;&ensp;&ensp;2. 目录默认为“C:\Program Files (x86)\Windows-Agent\ Windows-Agent.exe”，</br>
  &ensp;&ensp;&ensp;&ensp;2003 X86为“C:\Program Files\ Windows-Agent\ Windows-Agent.exe。</br>



**4. 运行程序（源端本地）**

安装、配置防火墙并重启后，点击桌面【Windows-agent】将其运行；

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image056.png ':size=10%')

?> 按以下格式要求填写：</br>
&ensp;&ensp;&ensp;HyperMotion访问地址：http://:HyperMotionIP:18766； </br>
&ensp;&ensp;&ensp;NAT地址：填写本地NAT地址（纯IP地址），若为空，则会默认使用本机IP作为参数，点击【启动】；

系统自动弹出 “Windows Agent正常启动”对话框，点击【是】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image057.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image058.png ':size=40%')

!>注：1.Windows Agent服务开始运行并注册到所选HyperMotion平台。此时，Windows Agent服务在后台运行，关闭Agent界面不会对服务有影响，如机器重启Windows Agent服务会自动启动；
 &ensp;&ensp;&ensp;2. Windows Agent服务启动后，可在HyperMotion主控台中看该注册的主机，请返回HyperMotion主控台查看并继续其他操作。
 
 ---
 
### 3.2 Linux Agent安装说明

**1. 执行下列命令自动完成安装**

```
#curl http://<HyperMotio的IP地址:10080>/softwares/getplusagent.sh | bash
```

**2. 执行以下命令查看Agent状态：**

```  
# egisplus-cli agent check
```

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image059.png ':size=60%')

**3. Agent安装成功后，Agent service和iSCSI service已启动，并且Agent也已自动注册，等待执行保护操作。**

!>注：Linux Agent服务启动后，可在HyperMotion主控台中看该注册的主机，请返回HyperMotion主控台查看并继续其他操作。

---

## 4  云平台认证信息获取（目标平台操作）

### 4.1  阿里云（公）

**1. Access Key 和Access Key Secret的获取**

登录阿里云控制台首页，依次点击【个人头像】→【accesskey管理】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/24.png ':size=90%')

点击【创建AccessKey】，创建成功后，点击【保存AK信息】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/25.png ':size=90%')


**2. 镜像ID获取**

管理控制台页面，选择【云服务器ECS】【镜像】，记录安装步骤所创建的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/23.png ':size=90%')

---

### 4.2  AWS

**1. Access Key 和Access Key Secret的获取**

登录AWS控制台首页，依次点击【个人头像】→【我的安全凭证】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/image057.png ':size=90%')

点击【创建访问密钥】，创建成功后保存密钥信息。



**2. 镜像ID获取**

管理控制台页面，选择【映像】-【AMI】，记录安装步骤所创建的Linux镜像ID及Windows镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aws/image058.png ':size=90%')

### 4.3  Azure

**1. 应用程序ID和租户ID**

登录Azure控制台首页，依次下图步骤，按要求注册

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image056.png ':size=90%')

注册完成后点开注册信息

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image057.png ':size=90%')

获取应用程序ID和租户ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image058.png ':size=90%')

**2. 应用程序密钥**

【Azure Active Directory】-【证书和密码】，

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image059.png ':size=90%')

**3. 订阅ID**

【仪表盘】-【所有资源】，点开所创建的虚拟机，获取绑定的订阅ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image060.png ':size=90%')
**4. 资源组**

【仪表盘】-【所有资源】，点开所创建的虚拟机，获取HyperGate所在的资源组

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/azure/image061.png ':size=90%')

---
### 4.4  腾讯云（公）


**1. Access Key 和Access Key Secret的获取**

登录腾讯云控制台首页，依次点击【账号头像】→【访问管理】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/image059.png ':size=90%')

点击【创API密钥管理】→【新建密钥】，创建成功后，点击【显示】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/image060.png ':size=90%')

**2. 镜像ID获取**

管理控制台页面，选择【云服务器ECS】→【镜像】，记录安装步骤所创建的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/Tencent/image061.png ':size=90%')

---

### 4.5  华为云（公）

**1. 镜像ID获取**

管理控制台页面，选择【弹性云服务器】【镜像服务】，点击镜像名称进入

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/TechWave/image057.png ':size=90%')

记录安装步骤所创建的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/TechWave/image058.png ':size=90%')

### 4.6  金山云

**1. Access Key 和Access Key Secret的获取**

登录金山云主账号控制台首页，依次点击【账号名称】→【accesskeys】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/image057.png ':size=90%')

点击【新建密钥】，创建成功后，点击【下载凭证】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/image058.png ':size=90%')


**2. 镜像ID获取**

管理控制台页面，选择【云服务器】【镜像】，记录名称的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/KingCloud/image059.png ':size=90%')


### 4.7  青云

**1. Access Key 和Access Key Secret的获取**

登录青云主账号控制台首页，依次点击【账号名称】→【API密钥】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image056.png ':size=90%')

点击【新建密钥】，创建成功后，点击【下载】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image057.png ':size=90%')


**2. 镜像ID获取**

管理控制台页面，选择【镜像】，记录名称的镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/qingcloud/image058.png ':size=90%')

---

### 4.8  天翼云

**1. Access Key 和Access Key Secret的获取**

登录天翼云主账号控制中心，依次点击【账号名称】→【我的凭证】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image056.png ':size=90%')

点击【访问密钥管理】→【新增访问密钥】，创建成功后，下载保存凭证

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image057.png ':size=90%')


**2. 镜像ID获取**

管理控制台页面，选择【镜像服务】→点击进入该镜像详细，记录镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/ecloud/image058.png ':size=90%')


---

### 4.9  UCloud

**1. 公钥和私钥的获取**

登录UCloud控制台首页，账户信息下选择【API密钥】，同时获取公钥和私钥

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image057.png ':size=90%')



**2. 项目ID的获取**

账户信息下选择【权限管理】，记录所使用项目的项目ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image058.png ':size=90%')

**3. 镜像ID获取**

管理控制台页面，选择【全部产品】-【云主机】-【镜像管理】，记录镜像ID

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/UCloud/image059.png ':size=90%')

