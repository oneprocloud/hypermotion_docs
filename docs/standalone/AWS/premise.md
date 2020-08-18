# 迁移环境部署前提准备

## 部署方案选型

HyperMotion主控平台安装部署提供以下两种介质，可以根据需求进行下载使用:<br/>

**可以部署在VMware平台以及物理机**
- 【[ISO镜像](standalone/aliyun/premise.md?id=ISO下载)】

**可以部署支持QCOW2镜像云环境进行使用**

- 【[云端QCOW2镜像](standalone/aliyun/premise.md?id=QCOW2镜像下载)】
HyperGate云端数据代理我们将提供QCOW2镜像方式进行安装部署<br/>

!> HyperGate如果通过 **「云端QCOW2镜像」**部署使用，那么与HyperMotion使用同一个云端镜像，无需重复进行下载

---

## 安装包下载

### ISO下载

?> **「HyperMotion主控平台」**可以安装部署在物理机或者VMware虚拟机，以下链接将提供ISO方式进行部署

[HyperMotion ISO镜像下载](http://office.oneprocloud.com:18888/iso/hypermotion/%e6%9d%ad%e5%b7%9e%e6%94%bf%e5%8a%a1%e4%ba%91/HM_IMG-191227-2020-03-19.raw)

### QCOW2镜像下载

!> **「HyperMotion主控平台」**与 **「HyperGate云端数据代理」**均使用同一个QCOW2镜像进行安装部署，镜像启动

[HyperMotion & HyperGate QCOW2镜像下载](http://office.oneprocloud.com:18888/iso/hypermotion/%e6%9d%ad%e5%b7%9e%e6%94%bf%e5%8a%a1%e4%ba%91/HM_IMG-191227-2020-03-19.raw)

### HyperDoor驱动适配镜像下载

**「HyperDoor驱动适配镜像」** 此镜像主要用途为在迁移数据同步到目标云端之后，在启动系统时将会使用 **「HyperDoor驱动适配镜像」**进行驱动适配操作，此镜像为临时ramdisk操作系统，在添加目标平台时将会使用到<br/>

[HyperDoor QCOW2镜像下载](http://office.oneprocloud.com:18888/iso/hypermotion/%e6%9d%ad%e5%b7%9e%e6%94%bf%e5%8a%a1%e4%ba%91/HM_IMG-191227-2020-03-19.raw)

---

## 迁移策略开通

### 网络策略

!> 迁移操作前，请务必完成此步骤，按照以下需求开通网络策略


1. 预定安装 **「HyperGate云端数据代理」**实例所在地域下已创建安全组，并确保安全组已放行以下端口

18090、3260、1222、222

2. 迁移所需开放的所有网络策略，请按照以下条目进行端口开放

?> **以下代名词说明：** </br>
</br>
**HyperMotion: 迁移主控平台**</br>
**HyperGate: 迁移云端数据代理**</br>
**VCenter/ESXI: 源端VMware环境作为源端进行迁移**</br>
**源端待迁移主机: 安装Agent进行迁移的虚拟机或物理机**</br>

|   | 源端         | 目标端       | 通信方向/开放端口（目标端）                    | 备注                                                         |
| - | -------------- | --------------- | ----------------------------------------------------------- | -------------------------------------------------------------- |
| 1 | HyperMotion    | HyperGate       | 单向：18090、3260、12222、22                               | 迁移组件程序                                             |
| 2 |                | VCenter         | 单向：443                                                | 作为迁移源端：认证端口                              |
| 3 |                | ESXI主机      | 单向：902                                                | 作为迁移源端：数据传输端口                        |
| 4 |                | 源端待迁移主机 | 单向：19981                                              | 源端为Agent方式                                           |
| 5 | HyperGate      | 目标云台API网络 | 单向：5000、35357、9696、8773、8774、8775、8776、9191、9292 | 场景：迁移目标端为私有云 例如：OpenStack，其他私有云视情况而定 |
| 6 | 源端待迁移主机 | HyperGate       | 单向：3260                                               | 源端待迁移主机为Agent方式（物理机、KVM/Xen虚拟机等） |
| 7 |                | HyperMotion     | 单向：18766，10080                                      |                                                                |


### 云端账户权限开通

!> 迁移操作前，请务必完成此步骤，按照以下需求配置迁移云账户所需权限

1. 该账号已开放所需权限
 
 - 按照条目对迁移账户进行所需权限开放

 |   | 目标云端 | 权限          | 权限条目        | 备注          |
 | - | -------- | --------------- | ------------------- | --------------- |
 | 1 | 阿里云 | 云服务器（ECS） | AliyunECSFullAccess | ECS实例管理权限 |
 | 2 |          | 专有网络（VPC） | AliyunVPCFullAccess | VPC网络管理权限 |

2. 预定实例安装所在地域下已创建专有网络VPC和交换机

3. 获取的镜像包已上传阿里云平台
 - HyperDoor QCOW2镜像包