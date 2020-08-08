# 云原生迁移平台API对接最佳实践
## 1、整体说明
### 1.1 云原生迁移平台的需求说明
迁移和容灾作为云管平台重要的一个模块，在多云环境下已经变得越来越重要。传统的云管平台中，更多的是通过云平台API接口对单一云平台进行纵向调度，即使进行多云的混合调度编排，但是仍然无法解决数据层面的互联互通问题。云迁移和容灾平台有效的打通了多云之间数据层面的互通问题，让用户自助式的完成在不同云平台之间的负载切换。<br />![Picture1.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/cloud_management.png ':size=50%')<br />[https://www.gartner.com/document/3873016](https://www.gartner.com/document/3873016) 

### 1.2 云原生迁移平台迁移需求
根据云迁移策略的定义，常见的七种策略有：重新托管（Rehosting）、更换平台（Replatforming）、重新购买（Repurchasing）、重构（Refactoring/Re-architecting）、退役（Retire）、保留（Retian）。<br />![image.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/migration_policy.png ':size=50%')<br />在混合云环境下，对于用户成本最低、效率最高的方式就是重新托管（Rehosting）方式，即原封不动照搬过来，用户从操作系统到应用系统都不会发生任何改变，可以在线迁移，迁移之后可以立即使用。
迁移和容灾作为云管平台重要的一个模块，在多云环境下已经变得越来越重要。传统的云管平台中，更多的是通过云平台API接口对单一云平台进行纵向调度，即使进行多云的混合调度编排，但是仍然无法解决数据层面的互联互通问题。云迁移和容灾平台有效的打通了多云之间数据层面的互通问题，让用户自助式的完成在不同云平台之间的负载切换。<br />![Picture1.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/cloud_management.png ':size=50%')<br />[https://www.gartner.com/document/3873016](https://www.gartner.com/document/3873016) 

### 1.2 云原生迁移平台迁移需求
根据云迁移策略的定义，常见的七种策略有：重新托管（Rehosting）、更换平台（Replatforming）、重新购买（Repurchasing）、重构（Refactoring/Re-architecting）、退役（Retire）、保留（Retian）。<br />![image.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/migration_policy.png ':size=50%')<br />在混合云环境下，对于用户成本最低、效率最高的方式就是重新托管（Rehosting）方式，即原封不动照搬过来，用户从操作系统到应用系统都不会发生任何改变，可以在线迁移，迁移之后可以立即使用。

### 1.3 云原生迁移平台需求定义

- 1、实现“搬家（Re-Host）“效果。
- 2、实现“热迁移“效果。在用户迁移时，采用块级别差量复制技术实现准“热迁移“，用户无须关机即可完成在线迁移。迁移过程中，用户业务系统不中断，保证业务连续性。
- 3、云原生“集成“能力。通过云平台接口驱动层完成与多云之间的对接，充分利用云上资源的特性，在不借助任何特殊设备情况下进行迁移。对云原生接口深度对接能力，除了对接基本主机、磁盘创建能力外，还应支持：内部网络地址指定、外部网络地址选择、单租户同步多租户资源转移、多租户（普通租户，非管理员权限）同步和启动、指定快照时间点多次验证等深度功能。
- 4、“被集成“能力。云迁移服务本身的功能全部以RESTful API方式提供给云管理平台或第三方应用，使得用户无须单独操作迁移平台，通过云管平台与办公流程联动，在资源配额满足需求的前提下，仅需几步简单配置便可在线完成迁移。
- 5、面向多租户设计。用户订阅迁移服务，自助完成迁移动作，无须管理员介入。
- 6、智能驱动适配，实现一键式迁移效果。迁移服务会智能的判断目标云平台的虚拟化类型，选择合适的磁盘、网卡等驱动进行驱动注入，保证迁移后的系统在目标云平台能够正常使用。<br />

## 2、云原生迁移平台使用场景

### 2.1 整体架构及对接方式

#### 2.1.1 整体架构

云管平台通过云原生迁移平台提供的RESTful API接口进行对接，调度迁移平台完成迁移操作。<br />

![Picture2.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/restful_api.png ':size=50%')

#### 2.1.2 对接流程
![duijie.svg](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/api/duijie.svg ':size=50%')

### 2.2 源端场景说明

#### 2.2.1 代理方式使用（Agent）
适用场景：用于物理机、公有云平台、私有化平台虚拟机的同步，Agent需要安装在用户操作系统内部，需要用户人为进行安装操作。目前Linux Agent使用脚本方式安装，用户需要登陆到待迁移主机内使用Root权限执行安装脚本即可；Windows Agent需要用户首先下载后执行安装并正确配置迁移平台地址后，才能正常使用。<br />对接建议：在云管平台对接使用时，需要显示的提示用户代理程序下载及安装方式。
<a name="M9Ncp"></a>
#### 2.2.2 无代理方式使用（Agentless）
适用场景：主要用于VMware平台虚拟机的同步，需要提供vCenter或者ESXi的鉴权信息，用于获取虚拟机列表及同步数据。<br />对接建议：在云管平台对接时，该信息应为云管平台相应的管理员填写后，普通租户直接进行迁移操作即可。
### 2.3 目标端场景说明
<a name="tGnPb"></a>
#### 2.3.1 OpenStack
<a name="BMnO0"></a>
##### 场景一：租户独享数据同步代理
适用场景：每个租户（OpenStack真实租户）建立独立的同步代理服务器，目前版本中该虚拟机的建立和开通还尚未支持自动化。<br />对接建议：在云管平台对接时，需要为目标租户建立云主机并安装相应的同步代理软件，并且正确配置租户的鉴权信息后，才能开始迁移。
<a name="jGBu1"></a>
##### 场景二：共享同步代理，启动时指定租户
适用场景：在共享租户（OpenStack真实租户）建议共享的同步代理服务器，该场景适用于对网络、租户配额等有严格要求的云平台，不希望在迁移过程中增加租户内的配置成本。该种方式下，同步过程在共享租户下完成，启动主机后到指定的目标租户。<br />对接建议：在云管平台对接时，只需要提前建议好共享同步代理及分配相应的权限即可完成后续的迁移流程。启动主机时，根据目标租户情况自动帮助用户选择或填充。
<a name="vdxHk"></a>
##### 场景三：迁移验证
适用场景：用于迁移前，系统在目标云平台的验证，用户可以选择指定的快照时间点进行验证工作。<br />对接建议：按需对接。
<a name="AAMys"></a>
##### 场景四：启动主机
启动主机可以作为迁移验证或者正式迁移使用，为了满足OpenStack平台的业务场景，提供如下场景支持：

- 场景一：指定规格、网络及安全组

对接建议：启动主机时可以选择云平台已经创建好的规格、网络及安全组。

- 场景二：指定迁移后的Fixed IP

对接建议：用于指定迁移的虚拟机在云平台中启动后的Fixed IP分配

- 场景三：指定分配迁移后的Floating IP

对接建议：从Floating IP资源池中绑定迁移后主机的Floating IP

- 场景四：卷快照方式或卷备份方式

对接建议：如果底层使用Ceph存储，使用卷快照方式会导致底层的卷存储依赖关系，所以在启动时可以选择卷快照方式或者卷备份方式解链，保证后续资源清理可以顺利进行。<br />如果使用的为商业存储，建议直接使用卷快照方式进行迁移验证或者正式启动，具体操作方式可以由云管平台建议。

#### 2.3.2 公有云

##### 场景一：租户独享数据同步代理
适用场景：每个租户（公有云租户）建立独立的同步代理服务器，目前版本中该虚拟机的建立和开通还尚未支持自动化。<br />对接建议：在云管平台对接时，需要为目标租户建立云主机并安装相应的同步代理软件，并且正确配置租户的鉴权信息后，才能开始迁移。
##### 场景二：迁移验证
适用场景：用于迁移前，系统在目标云平台的验证，用户可以选择指定的快照时间点进行验证工作。<br />对接建议：按需对接。
##### 场景三：启动主机
启动主机可以作为迁移验证或者正式迁移使用，提供如下场景支持：

- 场景一：指定规格、网络及安全组

对接建议：启动主机时可以选择云平台已经创建好的规格、网络及安全组。
### 2.4 其他场景说明
#### 2.4.1 用户体系
对接建议：迁移平台使用单用户模式，云管平台使用自身租户系统即可。
#### 2.4.2 授权管理
对接建议：迁移平台采用License管制方式，建议为系统进行一次性授权。
## 3、API接口使用说明
<a name="iWdlM"></a>
### 3.1 对象说明
| 类型 | 说明 |
| --- | --- |
| 用户鉴权(Users) | 用于获取鉴权信息，作为后续请求访问使用 |
| 源端管理(Sources) | 用于对待迁移的源端平台进行管理，主要针对无代理方式 |
| 目标管理(Targets) | 用于管理待迁移的目标端，这里主要指的是云平台，在其他应用场景中也可以作为存储概念使用 |
| 待迁移主机管理（Hosts） | 迁移流程管理中的对象，涉及迁移流程的推进和各种操作 |
| 任务管理（Jobs） | 用于管理迁移中产生的任务及进度追踪 |
| 授权管理（Licenses） | 用于对迁移授权进行管理 |
| 诊断管理（Diagnoses） | 用于迁移过程中的诊断管理，常作为异常检测时使用 |

<a name="fieRz"></a>
#### 3.2 接口请求时序图
![](https://cdn.nlark.com/yuque/__puml/060876749b952c9cf0ccd6a27f77d827.svg#lake_card_v2=eyJjb2RlIjoiQHN0YXJ0dW1sXG5hdXRvbnVtYmVyXG5cbmFjdG9yIFwi55So5oi3XCIgYXMgdXNlclxucGFydGljaXBhbnQgXCLlvoXov4Hnp7vkuLvmnLpcIiBhcyBob3N0XG5wYXJ0aWNpcGFudCBcIuS6keeuoeW5s-WPsFwiIGFzIGNtcFxucGFydGljaXBhbnQgXCLov4Hnp7vlubPlj7BcIiBhcyBtaWdyYXRpb25cblxuPT0g6YCJ5oup5b6F6L-B56e75Li75py6ID09XG51c2VyIC0-IGNtcDog6YCJ5oup5b6F6L-B56e755qE5Li75py6XG5jbXAgLT4gdXNlcjog5pi-56S66L-B56e75ZCR5a-8XG5cbj09IOmihOajgOafpSA9PVxuY21wIC0-IGhvc3Q6IOajgOafpeS4u-acuuaYr-WQpua7oei2s-i_geenu-adoeS7tlxuY21wIC0-IHVzZXI6IOi_lOWbnuaYr-WQpua7oei2s-i_geenu-adoeS7tu-8jOWmguaenOa7oei2s-i_m-WFpeS4i-S4gOatpVxubm90ZSBsZWZ0XG7lpoLmnpzkuLpBZ2VudOaWueW8j--8jOWImeeUseS6keeuoeW5s-WPsOi_m-ihjOajgOafpVxu5aaC5p6c5Li6Vk13YXJl5pa55byP77yM5Y-v5Lul5LuO5o6l5Y-j6I635Y-W6K-l5L-h5oGvXG5lbmQgbm90ZVxuXG49PSDms6jlhozkuLvmnLogPT1cbmNtcCAtPiB1c2VyOiDmj5DnpLrnlKjmiLfov5vooYxBZ2VudOWuieijhVxubm90ZSBsZWZ0XG7lpoLmnpzkuLpWTXdhcmXmlrnlvI_vvIzliJnml6DpobvmraTmraXpqqRcbmVuZCBub3RlXG51c2VyIC0-IGhvc3Q6IOWuieijhUFnZW505bm25rOo5YaMXG5jbXAgLT4gdXNlcjogQWdlbnTlt7Lnu4_ms6jlhozmiJDlip_vvIzlhYHorrjov5vlhaXkuIvkuIDmraVcblxuPT0g5ZCM5q2l5pWw5o2uID09XG51c2VyIC0-IGNtcDog5ZCM5q2l5pWw5o2uXG5jbXAgLT4gbWlncmF0aW9uOiDlkIzmraXmlbDmja4oNC40LjHmjqXlj6MpXG5cbmdyb3VwIFwi6I635Y-W5ZCM5q2l5pWw5o2u6L-b5bqmXCJcbmNtcCAtPiBtaWdyYXRpb246IOiOt-WPluWQjOatpei_m-W6pig0LjcuMSBvciA0LjcuM-aOpeWPoylcbmNtcCAtPiB1c2VyOiDmmL7npLrlvZPliY3ov5vluqZcbmVuZCBncm91cFxuXG49PSDlkK_liqgv6aqM6K-B5Li75py6ID09XG51c2VyIC0-IGNtcDog5ZCv5YqoL-mqjOivgeS4u-aculxuY21wIC0-IG1pZ3JhdGlvbjog5ZCv5YqoL-mqjOivgeS4u-acuig0LjUuMeaOpeWPoylcblxuZ3JvdXAgXCLojrflj5blkK_liqjov5vluqZcIlxuY21wIC0-IG1pZ3JhdGlvbjog6I635Y-W5ZCv5Yqo6L-b5bqmKDQuNy4xIG9yIDQuNy405o6l5Y-jKVxuY21wIC0-IHVzZXI6IOaYvuekuuW9k-WJjeWQr-WKqOi_m-W6plxuZW5kIGdyb3VwXG5cbj09IOi1hOa6kOa4heeQhiA9PVxudXNlciAtPiBjbXA6IOi1hOa6kOa4heeQhlxuY21wIC0-IG1pZ3JhdGlvbjog6LWE5rqQ5riF55CGKDQuNi4x5o6l5Y-jKVxuXG5ncm91cCBcIuiOt-WPlui1hOa6kOa4heeQhui_m-W6plwiXG5jbXAgLT4gbWlncmF0aW9uOiDojrflj5botYTmupDmuIXnkIbov5vluqYoNC435o6l5Y-jKVxuY21wIC0-IHVzZXI6IOaYvuekuuW9k-WJjei1hOa6kOa4heeQhui_m-W6plxuZW5kIGdyb3VwXG5cbkBlbmR1bWwiLCJ0eXBlIjoicHVtbCIsImlkIjoiNG9JSXoiLCJ1cmwiOiJodHRwczovL2Nkbi5ubGFyay5jb20veXVxdWUvX19wdW1sLzA2MDg3Njc0OWI5NTJjOWNmMGNjZDZhMjdmNzdkODI3LnN2ZyIsImhlaWdodCI6NDgwLCJjYXJkIjoiZGlhZ3JhbSJ9)<a name="gWEJC"></a>
## 4、API接口列表
**请求端口**: 18088<br />**请求BaseURL**：https://IP:18088/{URL}
### 4.1 鉴权接口
#### 4.1.1 获取访问接口Token
**接口请求方式**<br />POST /hypermotion/v1/users/token**<br />**接口描述**<br />获取接口访问token，有效期24小时。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |

**Body**

| 参数名称 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| username | string | 是 | "admin" | 用户名 |
| password | string | 是 | "admin_pass" | 密码 |
|  |  |  |  |  |

**参考示例**
```json
{
  "username": "admin",     // 用户名
  "password": "admin_pass"   // 密码
}
```
**返回数据**
```json
{
   "token": "0002000202354564545"
}
```
<a name="bDuxT"></a>
#### 4.1.2  修改默认用户密码
**接口请求方式**<br />PUT  /hypermotion/v1/users<br />**接口描述**<br />修改默认管理员密码<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**Body**

| 参数名称 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| old_password | string | 是 | "admin_pass" | 原始密码 |
| new_password | string | 是 | "admin" | 新密码 |
| check_password | string | 是 | "admin" | 确认密码 |

**参考示例**
```json
{
  "old_password": "admin_pass",  // 原始密码
  "new_password": "admin",       // 新密码
  "check_password": "admin"      // 确认密码
}
```
**返回数据**
```json
{
  "username": "admin"
}
```
<a name="o3ugM"></a>
### 4.2 环境准备接口
<a name="vrHYg"></a>
#### 4.2.1 添加目标平台链接接口
**接口请求方式**<br />POST  /hypermotion/v1/targets<br />**接口描述**<br />添加目标云平台链接到系统中。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Body**

| 参数名称 | 上级节点 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- | --- |
| type |  | string | 是 | "HyperGate" | 云平台类型 |
| config |  | object | 是 |  | 目标端配置 |
| port | config | integer | 是 | 18090 | HyperGate服务端口 |
| os_user_domain_id | config | string | 是 | "default" | User Domain ID |
| os_project_domain_id | config | string | 是 | "default" | Project Domain ID |
| cloud_type | config | string | 是 | "OpenStack" | HyperGate类型 |
| auth_url | config | string | 是 | "192.168.10.2" | HyperGate服务注册ip地址 |
| os_region_name | config | string | 是 | "RegionOne" | HyperGate平台域 |
| volume_availability_zone | config | string | 是 | "nova" | 存储可用区 |
| os_username | config | string | 是 | "zhaojun" | 用户名 |
| os_password | config | string | 是 | "Abc666111" | 密码 |
| os_project_name | config | string | 是 | "zhaojun" | 目标云平台项目名称 |
| os_auth_url | config | string | 是 | "http://192.168.10.201:5000/v3" | 目标云平台地址url |
| metadata |  | object | 是 |  |  |
| driver_name | metadata | string | 是 | "OpenStack" | 云平台类型 |

**参考示例**
```json
// 添加 openstack类型 HyperGate
{
    "type":"HyperGate",                    // 云平台类型
    "config":{
        "port":18090,                      // HyperGate服务端口
        "os_user_domain_id":"default",     // User Domain ID
        "os_project_domain_id":"default",  // Project Domain ID
        "cloud_type":"OpenStack",          // HyperGate类型
        "auth_url":"192.168.10.153",     // HyperGate服务注册ip地址
        "os_region_name":"RegionOne",      // HyperGate平台域
        "volume_availability_zone":"nova", // 存储可用区
        "os_username":"guohewei",          // 用户名
        "os_password":"Abc999",            // 密码
        "os_project_name":"guohewei",      // 目标云平台项目名称
        "os_auth_url":"http://192.168.10.201:5000/v3" // 目标云平台地址url
    },
    "metadata":{
        "driver_name":"OpenStack"  // 云平台类型
    }
}
```
**返回数据**
```json
{
  "code": 200,
  "message": "Successfully create target: OpenStack_192.168.10.127"
}
```
<a name="LYdmb"></a>
#### 4.2.2 获取目标端链接列表接口
**接口请求方式**<br />GET /hypermotion/v1/targets<br />**接口描述**<br />获取已添加的目标云平台链接列表数据。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| type | 否 | HyperGate | HyperGate: 获取 HyperGate类型的targets |

**<br />**返回数据**<br />目标端类型（target_status）：

- 正常（active）
- 失联 （disconnected）
- 创建中 （creating）
- 移除中 （removing）
- 创建失败（create_failed）
- 移除失败（remove_failed）
- 可使用 (available)
```json
// type=HyperGate
{
  "targets": {
    "data": [
      {
        "assign_size": 0,   
        "cloud_type": "OpenStack",   // 目标平台类型
        "is_doing": false,   
        "online": 1,                 // 0 源端不在线，1源端在线
        "status_icon": "done", 
        "target_display_name": "OpenStack_192.168.10.131", // 目标平台name
        "target_status": "active", // 目标端状态 参照上面目标端状态枚举
        "uuid": "24bb589a-225c-8ddef399d882"// 目标平台uuid
      }
    ]
  }
}
```
<a name="VLFJ7"></a>
#### 4.2.3 获取目标端链接详细信息
**接口请求方式**<br />GET  /hypermotion/v1/targets/:id<br />**接口描述**<br />获取已添加的目标云平台链接详细信息。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**路径参数** 

| 参数名称 | 示例 | 备注 |
| --- | --- | --- |
| id | 5e14e964-be05-44d4-80f5 | 目标平台uuid  |

**<br />**返回数据**
```json
// type=HyperGate
{   // HyperGate存储信息
    "Storage": {
        "data": [
            {
                "assign_size": 0, 
                "os_project_name": "guohewei", // 目标云平台项目名称
                "os_region_name": "RegionOne", // 目标云平台域
                "os_username": "guohewei",     // 用户名
                "status": "available", // 目标状态 参照获取目标端列表接口中，目标端状态枚举
                "target_ip": "192.168.10.153", // 目标云平台ip
                "target_name": "OpenStack_192.168.10.153", // 目标云平台名称
                "total_size": "1000 GB", 
                "type": "HyperGate",           // 目标端类型
                "used_size": 0, 
                "volume_availability_zone": "nova" // 存储可用区
            }
        ]
    }, 
    // HyperGate存储池信息
    "storage_pools": {
        "data": [
            {
                "assign_size": "0 GB", 
                "is_registered": true, // 是否可用
                "name": "ddd",         // 存储池名称
                "protocol": "iSCSI",   // Protocol
                "status": "available", // 存储池卷状态
                "total_size": "500 GB", 
                "used_size": "0 GB"
            }
        ]
    }, 
    // HyperGate 卷组信息
    "volume_groups": {
        "data": [
            {
                "Pool": "ddd", 
                "attach_status": "attached", 
                "h_status": "in-use", 
                "is_doing": false, 
                "name": "hvg_sync_k-node01-10.92", 
                "status": "in-use", 
                "status_icon": "done", 
                "uuid": "0f8d5395-173d-4f9b-9275-5cbbc32ac6c5"
            }
        ]
    }, 
    "volumes": { // HyperGate 卷组信息
        "data": [
            {
                "attach_status": "attached", 
                "capacity": "40.0GB", 
                "connector:host": "k-node01-10.92", 
                "name": "sync_vol_k-node01-10.92_k-node01-10.92_1.vmdk",  // j卷名称
                "source:pool_uuid": "ddd",                                //  
                "status": "in-use", 
                "uuid": "2604803c-b01f-45fe-b278-5baa5f2e5507"
            }
        ]
    }
}
```
<a name="aCaMO"></a>
#### 4.2.4 删除目标平台链接接口
**接口请求方式**<br />DELETE   /hypermotion/v1/targets/:id<br />**接口描述**<br />删除目标平台连接。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**路径参数** 

| 参数名称 | 示例 | 备注 |
| --- | --- | --- |
| id | 5e14e964-be05-44d4-80f5 | 目标平台uuid  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| force | 否 | force=true | 是否强制删除 |

**<br />**返回数据**
```json
{
   "code": 200,
   "data": null,
   "message": "Success delete targets connection: 06676817-97e0-4b84-a832-a6a978011dc4 "
}
```
<a name="z5vSk"></a>
#### 4.2.5 获取迁移目标(HyperGate)类型
**接口请求方式**<br />GET   /hypermotion/v1/targets/types<br />**接口描述**<br />获取当前系统中目标云平台有哪些类型。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**返回数据**
```json
{
   "target_types": [
      {	 // OpenStack存储类型
         "display_name": "OpenStack",  // 显示名称
         "query_name": "OpenStack"     // 请求名称
      }
   ]
}
```
<a name="VOTSg"></a>
### 4.3 添加主机接口
<a name="d0nmb"></a>
#### 4.3.1 注册主机接口
**接口请求方式**<br />POST  /hypermotion/v1/hosts/register<br />**接口描述**<br />将主机从源端注册到系统中， 以便将主机指定到云平台上，进行迁移。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**Body**

| 参数名称 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| ids | list | 是 |  | 主机 uuid 列表 |

**参考示例**
```json
{
    "ids":[   
        "10b7b25a-5e3b-463b-bdb3-26fe2cab83cb", // 主机uuid列表
        "16cd0750-55c6-49b2-a8f8-a6ab1d999cbc"
    ]
}
```
**返回数据**
```json
{
    "code": 200, 
    "data": [
        "10b7b25a-5e3b-463b-bdb3-26fe2cab83cb", // 注册主机uuid
        "16cd0750-55c6-49b2-a8f8-a6ab1d999cbc"
    ], 
    "message": "Success register hosts"
}
```
<a name="cr9EW"></a>
### 4.4 同步数据接口
<a name="ealUP"></a>
#### 4.4.1 同步数据接口
**接口请求方式**<br />POST  /hypermotion/v1/hosts<br />**接口描述**<br />同步主机数据到目标端, 可根据主机列表中is_sync字段判断是否可以同步数据。<br />is_sync字段参考获取主机列表接口返回数据(4.7接口)<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**Body**

| 参数名称 | 上级节点 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- | --- |
| ids |  | list | 是 |  | 主机 uuid 列表 |
| sync |  | object | 是 |  | 同步数据配置参数 |
| do_snapshot | sync | bool | 是 | true | 是否生成快照 |
| sync_mode | sync | string | 是 | "full" | "full": 全量，"incremental":增量 |
| transfer_speed | sync | integer | 否 | 0 | 注意：该功能目前只支持agent主机<br />同步限速，单位 Mbps，<br />1. 如果不设置限速，不传该字段或者值为null(默认使用上一次设置的值，如果第一次同步数据，则默认不限速)。<br />2. 如果不限速，值为0。<br />3. 如果限速，取值范围大于等于1的浮点数 |

**参考示例**
```json
{
  "ids": [       
    "3f947087-caed-427d-8d53-8c5e23cf2310",    // 主机uuid
    "292f59af-9617-48ea-9881-f65796935e14"
  ],
  "sync": {
    "do_snapshot": true,  // 是否生成快照
    "sync_mode": "full",  // "full": 全量，"incremental":增量
    "transfer_speed": 0   // 不限速
  }
}
```
**返回数据**
```json
{
    "code": 200, 
    "message": "Start synchronization of host resources"
}
```
<a name="t1qA1"></a>
### 4.5 启动主机接口
<a name="EBGyv"></a>
#### 4.5.1 启动主机接口
**接口请求方式**<br />POST  /hypermotion/v1/hosts/:id/action<br />**接口描述**<br />在目标云平台启动指定主机。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**路径参数**

| 参数名称 | 示例 | 备注 |
| --- | --- | --- |
| id | 5e14e964-be05-44d4-80f5 | 主机uuid |

**Body**
```json
// 目标平台 OpenStack 启动实例
{
    "boot":{
    
        // 以下为必须参数
        "project_name":"guohewei",        // 项目名称 
        "backup_type":"volume_snapshot",  // 启动方式 迁移测试(volume_snapshot)/迁移切换(volume_backup)
        "os_type":"Linux",                //系统类型 Linux/Windows
        "network_id":"2fd60fe7-de56-422", // 网络ID
        "availability_zone_id":"nova",    // 可用区ID
        "security_group_id":"401733-416", // 安全组ID
        "flavor_id":"bcf37edd-2ec2-462",  // 实例规格ID
        "snapshot_id":"885f8a27-f19111df" // 快照ID
        
        // 以下为可选参数
        "fixed_ip":"192.168.10.4",  // 固定启动主机IP地址，如果该IP已被占用则启动失败 
        "keypair_id":"",            // 密钥对ID
        "subnet_id":"8468e-8f9181", // 子网ID 
        "floating_ip_id":"",        // Floating IP ID
        "admin_pass":"123456", // 重置密码，此密码只针对安装cloud-init套件且目标端为OpenStack平台的实例生效，其他主机均不需要填写栏位，使用原账户密码登陆即可。
        
        "floating_ip_address":"",  // Floating IP
        "floating_network_id":"",  // Floating IP 所在的network ID
        "network_name":"public_vlan3", // 网络name
        "network_type":"floating",     // 网络类型
        "subnet_name":"public_vlan3_subnet",// 子网name
        "subnet_cidr":"192.168.10.0/24",    // 子网cidr
        "availability_zone_name":"nova",    // 可用区name
        "security_group_name":"default",    // 安全组name
        "flavor_name":"1core1G200G",        // flavor_name
        "flavor_ram":"1",                   // flavor_ram
        "flavor_vcpus":"1"                  // flavor_vcpu        
    }
}
// 目标平台 OpenStack 启动实例（使用自定义project）
{
    "boot":{
    
        // 以下为必须参数
        "project_name":"zhaojiangbo",   // 自定义project_name
        "project_domain_id":"default",  // 自定义project_domain_id
        "user_name":"zhaojiangbo",      // 自定义user_name
        "user_domain_id":"default",     // 自定义user_domain_id
        "user_password":"Abc999",       // 自定义用户密码
        "backup_type":"volume_snapshot",// 启动方式 迁移测试(volume_snapshot)/迁移切换(volume_backup)
        "os_type":"Linux",              //系统类型 Linux/Windows
        "network_id":"2fd60fe7-de56",   // 网络ID
        "availability_zone_id":"nova",  // 可用区ID
        "security_group_id":"424-9fd6", // 安全组ID
        "flavor_id":"bcf37ed-2ec2-462", // 实例规格ID
        "snapshot_id":"885f8a27-f19df"  // 快照ID
        
        // 以下为可选参数
        "fixed_ip":"192.168.10.4",  // 固定启动主机IP地址，如果该IP已被占用则启动失败 
        "keypair_id":"",            // 密钥对ID
        "subnet_id":"844e968e-b81", // 子网ID 
        "floating_ip_id":"",        // Floating IP ID
        "admin_pass":"123456", // 重置密码，此密码只针对安装cloud-init套件且目标端为OpenStack平台的实例生效，其他主机均不需要填写栏位，使用原账户密码登陆即可。
        
        "floating_ip_address":"",  // Floating IP
        "floating_network_id":"",  // Floating IP 所在的network ID
        "network_name":"public_vlan3",       // 网络name
        "network_type":"floating",           // 网络类型
        "subnet_name":"public_vlan3_subnet", // 子网name
        "subnet_cidr":"192.168.10.0/24",     // 子网cidr
        "availability_zone_name":"nova",     // 可用区name
        "security_group_name":"default",     // 安全组name
        "flavor_name":"1core1G200G",         // flavor_name
        "flavor_ram":"1",                    // flavor_ram
        "flavor_vcpus":"1"                   // flavor_vcpu  
    }
}
```
**返回数据**
```json
{
    "code": 200, 
    "message": "Start booting host"
}
```
<a name="sf80y"></a>
### 4.6 资源清理接口
<a name="EToKp"></a>
#### 4.6.1 清理资源接口
**接口请求方式**<br />POST  /hypermotion/v1/hosts<br />**接口描述**<br />指定清理主机，在目标端的同步数据，快照数据，注册数据。<br />可根据主机列表中is_clean字段判断是否可以清理资源。<br />is_clean字段参考获取主机列表接口返回数据(4.7接口)<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**Body**

| 参数名称 | 上级节点 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- | --- |
| ids |  | list | 是 |  | 主机 uuid 列表 |
| clean |  | object | 是 |  | 同步数据配置参数 |
| force | clean | bool | 是 | true | 不传入默认为false，强制删除置为true。 |

**参考示例**
```json
{
  "ids": [  
    "3b7890bb-e6f6-445e-aea1-b1ec13b265bc"    // 主机uuid
  ],
  "clean": {
      "force": false //不传入默认为false，强制删除置为true。
  }
}
```
**返回数据**
```json
{
    "code": 200,        
    "message": "Start delete of host resources"   // 返回message
}
```
<a name="Adq56"></a>
### 4.7 获取迁移主机列表接口
主机在迁移过程中有两个状态。一个是迁移状态（h_host_status），一个是启动状态（h_boot_status)，主机的健康状态（h_health_status）。
![](https://cdn.nlark.com/yuque/__puml/38333fd0e2bf853ad85f355fa74d8b03.svg#lake_card_v2=eyJjb2RlIjoiQHN0YXJ0dW1sXG5za2lucGFyYW0gc3RhdGUge1xuICBCYWNrZ3JvdW5kQ29sb3IgTGlnaHRZZWxsb3dcbiAgQmFja2dyb3VuZENvbG9yPDxib290X3N0YXR1cz4-IExpZ2h0Ymx1ZVxufVxuXG5zdGF0ZSDov4Hnp7vlr7nosaHmgLvmpoLopoHlm74ge1xuXG5cbiAgICBoX2hvc3Rfc3RhdHVzOuS4u-acuueKtuaAgVxuICAgIGhfaG9zdF9zdGF0dXMgLT4gaF9ob3N0X3N0YXR1c1xuXG4gICAgaF9ib290X3N0YXR1czrlkK_liqjlrp7kvovnirbmgIFcbiAgICBoX2Jvb3Rfc3RhdHVzIC0-IGhfYm9vdF9zdGF0dXNcbiAgICBzdGF0ZSBcImhfYm9vdF9zdGF0dXNcIiA8PGJvb3Rfc3RhdHVzPj5cblxuICAgIHN0YXRlIFwiYm9vdF9kb25lXCIgPDxib290X3N0YXR1cz4-XG4gICAgaG9zdF9yZWdpc3Rlcl9kb25lOiDms6jlhozlrozmiJBcbiAgICBzeW5jX3NuYXBzaG90X2RvbmU6IOWItuS9nOW_q-eFp-WujOaIkFxuICAgIGhvc3RfdW5yZWdpc3Rlcl9kb25lOiDop6PpmaTms6jlhozlrozmiJBcblxuICAgIFsqXSAtLT4gaG9zdF9yZWdpc3Rlcl9kb25lOiDms6jlhozkuLvmnLpcbiAgICBob3N0X3JlZ2lzdGVyX2RvbmUgLT4gaG9zdF91bnJlZ2lzdGVyX2RvbmU6IOazqOmUgOS4u-aculxuICAgIGhvc3RfcmVnaXN0ZXJfZG9uZSAtLT4gc3luY19zbmFwc2hvdF9kb25lOiDlkIzmraXmlbDmja4o5ZCr5Yi25L2c5b-r54WnKVxuJ1xuICAgIHN5bmNfc25hcHNob3RfZG9uZSAtLT4gYm9vdF9kb25lOiDlkK_liqjlrp7kvotcbiAgICBib290X2RvbmUgLS0-IHN5bmNfc25hcHNob3RfZG9uZTog5ZCM5q2l5pWw5o2uKOWQq-WItuS9nOW_q-eFpylcbiAgICBib290X2RvbmUgLT4gaG9zdF91bnJlZ2lzdGVyX2RvbmU6IOi1hOa6kOa4heeQhlxuICAgIGhvc3RfdW5yZWdpc3Rlcl9kb25lIC0tPiBbKl1cbn1cbkBlbmR1bWwiLCJ0eXBlIjoicHVtbCIsImlkIjoiaDZxM0wiLCJ1cmwiOiJodHRwczovL2Nkbi5ubGFyay5jb20veXVxdWUvX19wdW1sLzM4MzMzZmQwZTJiZjg1M2FkODVmMzU1ZmE3NGQ4YjAzLnN2ZyIsImNhcmQiOiJkaWFncmFtIn0=)![](https://cdn.nlark.com/yuque/__puml/280b54af067fac254c7ed8af95639917.svg#lake_card_v2=eyJjb2RlIjoiQHN0YXJ0dW1sXG5zdGF0ZSDkuLvmnLrnirbmgIFoX2hvc3Rfc3RhdHVzIHtcbiAgICBbKl0gLS0-IGhvc3RfcmVnaXN0ZXJfZG9uZTog5rOo5YaM5Li75py6XG4gICAgICAgIGhvc3RfcmVnaXN0ZXJfZG9uZTog5rOo5YaM5a6M5oiQXG4gICAgICAgIHN5bmNfZG9pbmc6IOWQjOatpeS4rVxuICAgICAgICBzeW5jX2ZhaWxlZDog5ZCM5q2l5pWw5o2u5aSx6LSlXG4gICAgICAgIGhvc3RfcmVnaXN0ZXJfZG9uZSAtLT4gc3luY19kb2luZzog5ZCM5q2l5pWw5o2uXG4gICAgICAgIGhvc3RfcmVnaXN0ZXJfZG9uZSAtLT4gaG9zdF91bnJlZ2lzdGVyX2RvaW5nOiDop6PpmaTms6jlhoxcblxuICAgICAgICBzeW5jX2RvaW5nIC0-IHN5bmNfZmFpbGVkOiDoh6rliqhcbiAgICAgICAgc3luY19mYWlsZWQgLT4gc3luY19kb2luZzog5ZCM5q2l5pWw5o2uXG4gICAgICAgIHN5bmNfZmFpbGVkIC0tPiBjbGVhbl9kb2luZzog5riF55CG6LWE5rqQXG4gICAgICAgIHN5bmNfZG9pbmcgLS0-IHN5bmNfc25hcHNob3RfZG9uZTog6Ieq5YqoXG4gICAgICAgIHN5bmNfc25hcHNob3RfZG9uZSAtLT4gY2xlYW5fZG9pbmc6IOa4heeQhui1hOa6kFxuICAgICAgICBzeW5jX3NuYXBzaG90X2RvbmU6IOWItuS9nOW_q-eFp-WujOaIkFxuXG5cbiAgICAgICAgY2xlYW5fZG9pbmcgLT4gY2xlYW5fZmFpbGVkOiDoh6rliqhcbiAgICAgICAgY2xlYW5fZmFpbGVkIC0-IGNsZWFuX2RvaW5nOiDmuIXnkIbotYTmupBcbiAgICAgICAgY2xlYW5fZG9pbmcgLS0-IGNsZWFuX2RvbmU6IOiHquWKqFxuXG4gICAgICAgIGNsZWFuX2RvaW5nOiDmuIXnkIbkuK1cbiAgICAgICAgY2xlYW5fZG9uZTog5riF55CG5oiQ5YqfXG4gICAgICAgIGNsZWFuX2ZhaWxlZDog5riF55CG5aSx6LSlXG5cbiAgICAgICAgaG9zdF91bnJlZ2lzdGVyX2RvaW5nOiDop6PpmaTms6jlhozkuK1cbiAgICAgICAgaG9zdF91bnJlZ2lzdGVyX2ZhaWxlZDog6Kej6Zmk5rOo5YaM5aSx6LSlXG4gICAgICAgIGhvc3RfdW5yZWdpc3Rlcl9kb25lOiDop6PpmaTms6jlhozlrozmiJBcblxuICAgICAgICBob3N0X3VucmVnaXN0ZXJfZmFpbGVkIC0-IGhvc3RfdW5yZWdpc3Rlcl9kb2luZzog6Kej6Zmk5rOo5YaMXG4gICAgICAgIGhvc3RfdW5yZWdpc3Rlcl9kb2luZyAtPiBob3N0X3VucmVnaXN0ZXJfZmFpbGVkOiDoh6rliqhcbiAgICAgICAgY2xlYW5fZG9uZSAtLT4gaG9zdF91bnJlZ2lzdGVyX2RvaW5nOiDop6PpmaTms6jlhoxcbiAgICAgICAgaG9zdF91bnJlZ2lzdGVyX2RvaW5nIC0tPiBob3N0X3VucmVnaXN0ZXJfZG9uZTog6Ieq5YqoXG4gICAgICAgIGhvc3RfdW5yZWdpc3Rlcl9kb25lIC0tPiBbKl1cbn1cbkBlbmR1bWwiLCJ0eXBlIjoicHVtbCIsImlkIjoieEliSGQiLCJ1cmwiOiJodHRwczovL2Nkbi5ubGFyay5jb20veXVxdWUvX19wdW1sLzI4MGI1NGFmMDY3ZmFjMjU0YzdlZDhhZjk1NjM5OTE3LnN2ZyIsImNhcmQiOiJkaWFncmFtIn0=)![](https://cdn.nlark.com/yuque/__puml/729e0f87c49033159c8cc1e8afc77eab.svg#lake_card_v2=eyJjb2RlIjoiQHN0YXJ0dW1sXG5cbnN0YXRlIOWQr-WKqOeKtuaAgWhfYm9vdF9zdGF0dXMge1xuICAgIFsqXSAtLT4gbm90X2Jvb3RcbiAgICBub3RfYm9vdDog5pyq5ZCv5YqoXG4gICAgYm9vdF9kb2luZzog5ZCv5Yqo5LitXG4gICAgYm9vdF9mYWlsZWQ6IOWQr-WKqOWksei0pVxuICAgIGJvb3RfZG9uZTog5ZCv5Yqo5a6M5oiQXG5cbiAgICBub3RfYm9vdCAtLT4gYm9vdF9kb2luZzog5ZCv5Yqo5Li75py6XG4gICAgYm9vdF9kb2luZyAtPiBib290X2ZhaWxlZDog6Ieq5YqoXG4gICAgYm9vdF9mYWlsZWQgLT4gYm9vdF9kb2luZzog5ZCv5Yqo5Li75py6XG4gICAgYm9vdF9kb2luZyAtLT4gYm9vdF9kb25lOiDlkK_liqjmiJDlip9cbiAgICBib290X2RvbmUgLS0-IFsqXVxufVxuQGVuZHVtbCIsInR5cGUiOiJwdW1sIiwiaWQiOiI3MUFadCIsInVybCI6Imh0dHBzOi8vY2RuLm5sYXJrLmNvbS95dXF1ZS9fX3B1bWwvNzI5ZTBmODdjNDkwMzMxNTljOGNjMWU4YWZjNzdlYWIuc3ZnIiwiY2FyZCI6ImRpYWdyYW0ifQ==)
<br />**主机状态（h_host_status）如下：**<br />        host_register_done（注册完成）<br />        host_unregister_doing (解除注册中)<br />        host_unregister_done（解除注册完成）<br />        host_unregister_failed  (解除注册失败)<br />        sync_doing(同步中）<br />        sync_failed (同步数据失败)<br />        sync_snapshot_done (制作快照完成）<br />        clean_doing(清理中）<br />  clean_done(清理完成）<br />        clean_failed（清理失败）         <br />**启动状态（h_boot_status) 如下：**<br />        not_boot(未启动)<br />        boot_doing(启动中）<br />        boot_failed(启动失败)<br />        boot_done(启动完成）        <br />**主机健康状态（h_health_status）如下：**<br />  active  （正常）<br />  disconnected （失联）
<a name="4igT7"></a>
#### 4.7.1 获取迁移主机列表接口
**接口请求方式**<br />GET /hypermotion/v1/hosts<br />**接口描述**<br />获取迁移主机列表。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| page | 否 | 1 | page=1, 返回第一页数据 |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量 |
| target_platform | 否 | OpenStack / H3CCloudOS / AWSEBS / ZStack / Aliyun / TencentCloud / AzureCloud / HuaweiCloud / JinshanCloud / OpenStackImageBootV2 / PinganCloud / QingCloud | target_platform=OpenStack 获取目标端为OpenStack类型的主机 |
| ids | 否 | id1,id2,id3 | 获取指定id的主机列表<br />用逗号分割ID |
| macs | 否 | mac1,mac2,mac3 | 获取指定MAC的主机列表<br />用逗号分割mac |

**返回数据**
```json
{
   "page_size": 10,
   "total": 1,
   "data": [
      {
         "boot_icon": null,
         "boot_status": "not_boot",   // 主机启动状态
         "description": null,
         "detail": null,
         "detail_data": {
            "percent": 49,         // 已同步数据百分比
            "remaining_time": "2Minute(s)19Sec(s)",// 剩余同步时间
            "speed": "14Mbps",    // 当前同步速度
            "sync_detail": "Data syncing:49% Total:512MB synced:252MB Speed:14Mbps Remain time:0:2:19",
            "sync_total": "512MB", // 总需同步数据量
            "synced": "252MB"      // 已同步量
          },
         "h_boot_status": "not_boot",  // 主机启动状态，不会被国际化
         "h_health_status": "active",  // 主机健康状态，不会被国际化
         "h_host_status": "sync_snapshot_done",// 主机状态，不会被国际化
         "h_sync_status": "sync_snapshot_done",// 主机同步状态，不会被国际化，页面中显示为任务状态
         "has_success_snapshot": true,
         "health_icon": "done",
         "health_status": "active", // 主机健康状态
         "host_icon": "done",
         "host_name": "llx-windows2003",     // 主机名称
         "host_status": "sync_snapshot_done",// 主机状态
         "host_type": "vmware",              // 主机源端类型
         "id": "f2e9ab71-cda6-994e4b440360", // 主机uuid
         "ip_address": null,    // 主机ip
         "is_clean": true,      // 是否可以执行【清理资源】操作
         "is_doing": false,     // 主机是否正在执行操作中
         "is_next_step": false, // 是否可以执行【下一步】操作
         "is_stop_sync": true,  // 是否可以执行【停止同步】操作
         "is_sync": false,      // 是否可以执行【同步数据】操作
         "last_snapshots_at": "2019-12-31T01:41:26Z", // 上一次打快照时间
         "license_id": "495bcb89-7778", // 绑定的license uuid 
         "license_valid": true, // 绑定的license是否在有效期，如果为false，继续同步将再次消耗一个license
         "mac_address": "00:50:56:9f:21:4c", // 主机的MAC地址
         "snapshots": [
            {
              "created_at": "2020-01-02T03:00:10Z",  // 快照时间
              "size": "0"
              "id": "626c9cbf-2dfa-4add-986829072",  // 快照uuid
              "snapshot_name": "HyperMotion-20200102T110011",// 快照名称
              "status": "create_done", // 快照状态 创建中("create_doing")/创建失败("create_failed")/创建成功("create_done")
            }
          ],
         "storage_id": "6b94f79a-c1ad4941cfed", // 关联目标端HyperGate uuid
         "sync_icon": "done",
         "sync_status": "sync_snapshot_done",  // 主机同步状态
         "system_type": "Windows",             // 主机系统类型
         "target_name": "OpenStack_192.168.xx",// 目标云平台名称
         "task_id": null                        // 失败任务uuid
      }
   ]
}
```
<a name="QNBcG"></a>
#### 4.7.1 获取步骤1的迁移主机列表（注册主机列表）
**接口请求方式**<br />GET /hypermotion/v1/hosts?status=register<br />**接口描述**<br />获取注册完成的迁移主机列表（第1步主机列表接口）。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| page | 否 | 1 | page=1, 返回第一页数据 |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量 |
| status | 是 | status=register | status=register 获取完成注册的迁移主机列表 |
| target_platform | 否 | OpenStack / H3CCloudOS / AWSEBS / ZStack / Aliyun / TencentCloud / AzureCloud / HuaweiCloud / JinshanCloud / OpenStackImageBootV2 / PinganCloud / QingCloud | target_platform=OpenStack 获取目标端为OpenStack类型的主机 |
| kw | 否 | 1G | 作为搜索使用，仅限搜索主机名称 |

**返回数据**
```json
{
  "page_size": 10, 
  "total": 1,
  "data": [
    {
      "created_at": "2019-06-30T04:11:48Z", // 添加主机时间
      "h_health_status": "active",   // 主机健康状态，不会被国际化
      "h_host_status": "host_register_done",// 主机状态，不会被国际化
      "health_icon": "done", 
      "health_status": "active",            // 主机健康状态
      "host_icon": "done", 
      "host_name": "SUSE11SP2_5G",          // 主机名称
      "host_status": "host_register_done",  // 主机状态
      "host_type": "vmware",                // 主机源端类型
      "id": "a1d1032a-8bd1-4f76-bdd6-ebd06a25cc7e", // 主机uuid
      "ip_address": null,                   // 主机ip
      "is_clean": true,              // 是否可以执行清理资源操作
      "is_doing": false,             // 主机是否正在执行操作中
      "sync_required_volumes": 3     // 同步主机需要创建的卷个数
      "system_type": "Linux"         // 主机系统类型
    }
  ]
}
```
<a name="0Bu2c"></a>
#### 4.7.3 获取步骤2的迁移主机列表（同步主机列表）
**接口请求方式**<br />GET /hypermotion/v1/hosts?status=sync<br />**接口描述**<br />获取同步步骤中的迁移主机列表。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| page | 否 | 1 | page=1, 返回第一页数据 |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量 |
| status | 是 | status=sync | status=sync <br />获取完成注册的迁移主机列表 |
| target_platform | 否 | OpenStack / H3CCloudOS / AWSEBS / ZStack / Aliyun / TencentCloud / AzureCloud / HuaweiCloud / JinshanCloud / OpenStackImageBootV2 / PinganCloud / QingCloud | target_platform=OpenStack<br />获取目标端为OpenStack类型的主机 |
| kw | 否 | 1G | 作为搜索使用，仅限搜索主机名称 |

**返回数据**
```json
{
   "page_size": 10, 
   "total": 1,
   "data": [
      {
         "boot_icon": "None",
         "boot_status": "not_boot",   // 主机启动状态
         "description": null,
         "detail": null,
         "detail_data": {
            "percent": 49,         // 已同步数据百分比
            "remaining_time": "2Minute(s)19Sec(s)",// 剩余同步时间
            "speed": "14Mbps",    // 当前同步速度
            "sync_detail": "Data syncing:49% Total:512MB synced:252MB Speed:14Mbps Remain time:0:2:19",
            "sync_total": "512MB", // 总需同步数据量
            "synced": "252MB"      // 已同步量
          },
         "h_boot_status": "not_boot",  // 主机启动状态，不会被国际化
         "h_health_status": "active",  // 主机健康状态，不会被国际化
         "h_host_status": "sync_snapshot_done",// 主机状态，不会被国际化
         "h_sync_status": "sync_snapshot_done",// 主机同步状态，不会被国际化，页面中显示为任务状态
         "has_success_snapshot": true,
         "health_icon": "done",
         "health_status": "active", // 主机健康状态
         "host_icon": "done",
         "host_name": "llx-windows2003",     // 主机名称
         "host_status": "sync_snapshot_done",// 主机状态
         "host_type": "vmware",              // 主机源端类型
         "id": "f2e9ab71-cda6-994e4b440360", // 主机uuid
         "ip_address": "None",  // 主机ip
         "is_clean": true,      // 是否可以执行【清理资源】操作
         "is_doing": false,     // 主机是否正在执行操作中
         "is_next_step": false, // 是否可以执行【下一步】操作
         "is_stop_sync": true,  // 是否可以执行【停止同步】操作
         "is_sync": false,      // 是否可以执行【同步数据】操作
         "last_snapshots_at": "2019-12-31T01:41:26Z", // 上一次打快照时间
         "license_id": "495bcb89-7778", // 绑定的license uuid 
         "license_valid": true, // 绑定的license是否在有效期，如果为false，继续同步将再次消耗一个license
         "snapshots": [
            {
              "created_at": "2020-01-02T03:00:10Z",  // 快照时间
              "size": "0"
              "id": "626c9cbf-2dfa-4add-986829072",  // 快照uuid
              "snapshot_name": "HyperMotion-20200102T110011",// 快照名称
              "status": "create_done", // 快照状态 创建中("create_doing")/创建失败("create_failed")/创建成功("create_done")
            }
          ],
         "storage_id": "6b94f79a-c1ad4941cfed", // 关联目标端HyperGate uuid
         "sync_icon": "done",
         "sync_status": "sync_snapshot_done",  // 主机同步状态
         "system_type": "Windows",             // 主机系统类型
         "target_name": "OpenStack_192.168.xx",// 目标云平台名称
         "task_id": null                        // 失败任务uuid
      }
   ]
}
```
<a name="oYiqH"></a>
#### 4.7.4 获取步骤4的迁移主机列表（启动主机列表）
**接口请求方式**<br />GET /hypermotion/v1/hosts?status=boot<br />**接口描述**<br />获取启动步骤中的迁移主机列表。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| page | 否 | 1 | page=1, 返回第一页数据 |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量 |
| status | 是 | status=boot | status=boot <br />获取完成注册的迁移主机列表 |
| target_platform | 否 | OpenStack / H3CCloudOS / AWSEBS / ZStack / Aliyun / TencentCloud / AzureCloud / HuaweiCloud / JinshanCloud / OpenStackImageBootV2 / PinganCloud / QingCloud | target_platform=OpenStack<br />获取目标端为OpenStack类型的主机 |
| kw | 否 | 1G | 作为搜索使用，仅限搜索主机名称 |

**返回数据**
```json
{
  "page_size": 10, 
  "total": 2,
  "data": [
    {
      "boot_icon": "done", 
      "boot_status": "System booting done",      // 主机启动状态
      "description": null, 
      "detail": null, 
      "detail_data": { 
        "percent": 49,                           // 已同步数据百分比
        "remaining_time": "2Minute(s)19Sec(s)",  // 剩余同步时间
        "speed": "14Mbps",                       // 当前同步速度
        "sync_detail": "Data syncing:49% Total:512MB synced:252MB Speed:14Mbps Remain time:0:2:19",
        "sync_total": "512MB",                   // 总需同步数据量
        "synced": "252MB"                        // 已同步量
      },
      "h_boot_status": "not_boot",  // 主机启动状态，不会被国际化
      "h_health_status": "active",  // 主机健康状态，不会被国际化
      "h_host_status":"sync_snapshot_done",// 主机状态，不会被国际化
      "h_sync_status": "sync_snapshot_done", // 主机同步状态，不会被国际化，页面中显示为任务状态
      "has_success_snapshot": true, 
      "health_icon": "done", 
      "health_status": "active",                 // 主机健康状态
      "host_icon": "done", 
      "host_name": "jc-Redhat6.3_5G_LVM",        // 主机名称
      "host_status": "sync_snapshot_is_done",    // 主机状态
      "host_type": "vmware",                     // 主机源端类型
      "id": "9fb107cd-8e02-41d4-88c5-536a60475c9a",  // 主机uuid
      "ip_address": null,                        // 主机ip
      
      "is_clean": true,             // 是否可以执行【清理资源】操作
      "is_doing": false,            // 主机是否正在执行操作中
      "is_stop_sync": true,         // 是否可以执行【停止同步】操作
      "is_sync": false,             // 是否可以执行【同步数据】操作
      "last_project_name": "guohewei", // 上次启动使用的project_name
      "last_snapshots_at":"2019-12-31T01:41:26Z",// 上一次打快照时间
      "license_id": "c46def63-bf8c7ff6f6fa", // 绑定的license uuid 
      "license_valid": false,  // 绑定的license是否在有效期，如果为false，继续操作将再次消耗一个license
      "snapshots": [
        {
          "created_at": "2020-01-02T03:00:10Z", // 快照时间
          "size": "0"
          "id": "626c9cbf-2dfa-4add4829072",    // 快照uuid
          "snapshot_name":"HyperMotion-20200102T110011",// 快照名称
          "status": "create_done", // 快照状态 创建中("create_doing")/创建失败("create_failed")/创建成功("create_done") 
        }
      ],
      "storage_id": "aa93e297-3d4fc6",// 关联目标端HyperGate uuid
      "sync_icon": "done", 
      "sync_status": "sync_snapshot_is_done",  // 主机同步状态
      "system_type": "Linux",                  // 主机系统类型
      "target_name": "OpenStack_192.168.10.153", // 目标云平台名称
      "task_id": null                            // 失败任务uuid
      "cloud_instance_id": "9fb107cd-8e02-41d4-88c5-536a60475c9a",  // 启动后，OpenStack中虚拟机的UUID
    }
  ]
}
```
<a name="iQofa"></a>
#### 4.7.5 获取迁移主机详细信息接口
**接口请求方式**<br />GET  /hypermotion/v1/hosts/:id<br />**接口描述**<br />获取迁移主机详细信息。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**路径参数** 

| 参数名称 | 示例 | 备注 |
| --- | --- | --- |
| id | 5e14e964-be05-44d4-80f5 | 主机uuid  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| sheet | 是 | base &#124; storage &#124; snapshot | 基本信息，存储，快照 |
| page | 否 | 1 | page=1 返回第一页数据 (获取快照信息使用) |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量<br />(获取快照信息使用) |

**返回数据**
```json
// sheet=base 
{
  "host_detail": {
    "primary_information": {
      "data": {
        "aa_os_type": {   // 系统类型
          "title": "OS-Type", 
          "value": "Windows"
        }, 
        "boot_mode": {    // 启动方式
          "title": "Boot Mode", 
          "value": "bios"
        }, 
        "flavor_ram": {   // 内存
          "title": "RAM", 
          "value": "4.0GB"
        }, 
        "flavor_vcpus": {  // vcpu 个数
          "title": "vCPU", 
          "value": "1U"
        }, 
        "host_type": {    // 源端类型
          "title": "Source Type", 
          "value": "vmware"
        }, 
        "nics_ip": {     // IP地址
          "title": "IP Address", 
          "value": "None"
        }, 
        "nics_mac": {   // MAC地址
          "title": "Mac Address", 
          "value": "00:50:56:9f:63:72"
        }, 
        "nics_name": {   // 网卡
          "title": "Interface", 
          "value": "Nic-0"
        }, 
        "nisc_mask": {   // 子网掩码
          "title": "Net Mask", 
          "value": "None"
        }, 
        "os_version": {  // 系统版本
          "title": "Version", 
          "value": "Microsoft Windows Server 2012 (64-bit)"
        }, 
        "sync_strategies": {  // 同步策略
          "title": "Sync policy", 
          "value": "Close"
        }
      }, 
      "health_status": "active", 
      "title": "Primary Information"
    }
  }
}
```


```json
// sheet=storage 
{
  "description": "Storages", 
  "disk": {                                 // 磁盘信息
    "data": [
      {
        "created_at": "2019-06-30T04:11:48.000000", 
        "deleted": false, 
        "deleted_at": "None", 
        "disk_index": 0,                    // 编号
        "disk_type": "System Disk",         // 磁盘类型 系统盘(System Disk)/ 数据盘(Data Disk)
        "host_id": "6228a336-61e1-47b6-af18-48ec3a39b6c0",  
        "id": "fd7eb4fa-2a94-4d3297917fd",  // 磁盘UUID
        "is_boot_disk": true,               // 是否为系统盘
        "is_protected": true, 
        "name": "SUSE11SP2_5G.vmdk",        // 磁盘名称
        "serial": "6000C291-1187-b1b50326", // 磁盘序列号
        "size": "5.0G",                     // 磁盘大小
        "updated_at": "None"，
      }
    ]
  },
  "volume": {   // 卷信息
    "data": [
      {
        "corresponding_disk": "centos6.7_JC.vmdk", // 对应磁盘名称
        "name": "sync_vol_centos6.7_JC.vmdk",      // 卷名称
        "status": "in-use",                        // 卷状态
        "storages": "OpenStack_192.168.10.157/HyperGate_Pool", // 存储/存储池
        "uuid": "8c9a3c46-c1c5-480e-6a8e1321"      // 卷的uuid
      }
    ]
	}	
}
```


```json
// sheet=snapshot
{
  "data": [  // 快照列表数据
    {
      "created_at": "2020-01-02T03:00:10Z",         // 创建时间
      "id": "626c9cbf-2dfa-4add-9fdf-18ec84829072", // 快照ID
      "is_available": true,                         // 快照是否可用
      "size": 0,                                    // 快照大小
      "snapshot_name": "HyperMotion-20200102T110011", 
      "display_is_available": "true"
      "status": "create_done", // 快照状态 创建中("create_doing")/创建失败("create_failed")/创建成功("create_done")
    }
  ],
  "sync_strategy": {
    "do_snapshot": true,            // 同步完成是否打快照
    "snapshot_auto_trigger": false, // true--> 同步策略已启用，false--> 同步策略已停止
    "snapshot_interval": 1,         // 同步间隔
    "snapshot_interval_unit": "2",  // 注意：字符串类型， 同步间隔单位"1" --> 分钟  "2" --> 小时 "3" --> 日
    "snapshot_quota": 32,           // 快照配额
    "snapshot_start_time":"2020-01-02T06:57:14Z",// 同步策略启用时间
    "transfer_speed": 0             // 1. 值为0表示不限速； 2. 如果限速，取值范围大于等于1的浮点数
  }, 
  "total": 1,
  "page_size": 10
}
```
<a name="C4wx9"></a>
### 4.8 其他接口
<a name="7EoW4"></a>
#### 4.8.1 获取可指定目标平台列表接口
**接口请求方式**<br />GET /hypermotion/v1/targets<br />**接口描述**<br />获取主机可以指定的云平台列表信息。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| cloud_type | 否 | OpenStack &#124; H3CCloudOS &#124; AWSEBS &#124; ZStack &#124; Aliyun &#124; TencentCloud &#124; AzureCloud &#124; HuaweiCloud &#124; JinshanCloud &#124; OpenStackImageBootV2 &#124; PinganCloud &#124; QingCloud | cloud_type=OpenStack 获取OpenStack类型的HyperGate存储 |

**返回数据**
```json
{
  "targets": {
    "storages": [  // 指定平台列表
      {
        "pools": [
          {
            "pool_display_name": "HyperGate_Pool",// 存储池名称   
            "pool_uuid": "e96195b2-6d7dfdf1",    // 存储池uuid
            "storage_id": "24bb589a-225c-882"    // 存储uuid            
          }
        ], 
        "storage_display_name": "OpenStack_192.168.10.131(Available volumes 18)",   
        "storage_id": "24bb589a-225c-882",          // 存储uuid
        "storage_name": "OpenStack_192.168.10.131", // 存储名称
        "volumes_allocated_num": 2, // 已挂载卷数量
        "volumes_unused_num": 18  // 剩余卷数据
      }
    ]
  }
}
```
<a name="vqnl8"></a>
#### 4.8.2 指定平台
**接口请求方式**<br />PUT /hypermotion/v1/hosts/target_platform<br />**接口描述**<br />指定主机要迁移的目标平台。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Body**

| 参数名称 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| ids | list | 是 |  | 主机 uuid 列表 |
| storage_id | string | 是 | "4150336a-e38b" | 存储uuid |
| storage_name | string | 否 | "OpenStack_192.168.10.145" | 存储名称 |
| pool_id | string | 是 | "97095f8d-dd47-47a8" | 存储池uuid |
| pool_name | string | 否 | "HyperGate_Pool" | 存储池名称 |
| step | string | 是 | "2" | 指定平台后主机进入同步数据列表， 此值为固定值 |

**参考示例**
```json
{
  "ids": [ // 主机 uuid 列表
    "3f947087-caed-427d-8d53-8c5e23cf2310",
    "292f59af-9617-48ea-9881-f65796935e14"
  ],
  "storage_id": "4150336a-e38b-417f-32bbc05", // 存储uuid
  "storage_name": "OpenStack_192.168.10.145", // 存储名称
  "pool_id": "97095f8d-dd47-47a8-970a-c22a97a81836", // 存储池uuid
  "pool_name": "HyperGate_Pool",   // 存储池名称
  "step": "2"   // 指定平台后主机进入同步数据列表， 此值为固定值 
}
```
**返回数据**
```json
{
  "code": 200,
  "message": "Successful assign host on platform"   
}
```
<a name="U5v3u"></a>
#### 4.8.3 将主机由同步数据移到启动主机（下一步）
**接口请求方式**<br />POST  /hypermotion/v1/hosts<br />**接口描述**<br />将同步完成的主机，移入启动主机列表。<br />可根据主机列表中is_next_step字段判断是否可以执行下一步操作。<br />is_next_step字段参考获取主机列表接口返回数据(4.7接口)<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |  |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 | 访问token |

**Body**

| 参数名称 | 上级节点 | 参数类型 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- | --- |
| ids |  | list | 是 |  | 主机 uuid 列表 |
| next_step |  | object | 是 |  | 同步数据配置参数 |
| step | next_step | string | 是 | "4" | "4" 表示启动主机列表 |

**参考示例**
```json
{
  "ids": [             // 主机 uuid 列表
    "717c124f-a52a-429e-b8b9-1c8ea7e15854"
  ],
  "next_step": {
    "step": "4"      //  "4" 表示启动主机列表
  }
}
```
**返回数据**
```json
{
   "code": 200,
   "message": "Can start the migration"
}
```
<a name="sp5X9"></a>
#### 4.8.4 获取任务列表接口
**接口请求方式**<br />GET /hypermotion/v1/jobs<br />**接口描述**<br />获取任务列表信息。<br />**请求参数**<br />**Headers**

| 参数名称 | 参数值 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- | --- |
| X-AUTH-TOKEN |  | 是 | 0002000202354564545 |  |

**Query**

| 参数名称 | 是否必须 | 示例 | 备注 |
| --- | --- | --- | --- |
| status | 否 | all / working / complete | 状态为所有/进行中/完成 |
| page | 否 | 1 | page=1, 返回第一页所有jobs |
| page_size | 否 | 10 | page_size=10，每页返回的结果数量 |
| owner | 否 | CentOS7.4_121 | 过滤主机名称，即任务所属者 |
| job_type | 否 | 参考任务类型返回数据接口 | 过滤任务类型 |
| id | 否 | 15df50df-313f-4135 | 过滤主机uuid |

**返回数据**
```json
{	 
   "page_size": 10,
   "total": 63,
   "data": [
      {
         "description": "Register new host",
         "detail": "Done",  // 任务详情
         "detail_data": "None",
         "detail_icon": "done",
         "end_at": "2019-06-27T11:05:47Z", // 任务结束时间
         "event_id": "6f96f9cc-8102-47fd-ac3f-116e07e16c6f",
         "h_status": "done",
         "host": "Ray_win7_10.62", // 任务所属主机
         "job_status": "done",  // 任务状态
         "job_type": "Register",  // 任务类型
         "source_id": "835c9517-6a0f-4750-9ca7-b5091452be6d", // 任务所属主机uuid
         "source_type": "host",
         "start_at": "2019-06-27T11:05:47Z", // 任务开始时间
         "task_id": "05efaa67-81c8-42ea-a367-806ae87b606e", // 任务uuid
         "updated_at": "2019-06-27T11:05:47Z" // 任务更新时间
      },
      {
         "description": "Register new host",
         "detail": "Done",
         "detail_data": "None",
         "detail_icon": "done",
         "end_at": "2019-06-27T11:05:46Z",
         "event_id": "01fb17e5-1bd4-4e0c-8291-4e4275cb23b5",
         "h_status": "done",
         "host": "Redhat6.6_8G",
         "job_status": "done",
         "job_type": "Register",
         "source_id": "c80addac-b190-4f8e-9cf9-50cf695350b6",
         "source_type": "host",
         "start_at": "2019-06-27T11:05:46Z",
         "task_id": "5ae569a0-d3c7-434e-b0bf-c4a12c11e4d8",
         "updated_at": "2019-06-27T11:05:46Z"
      }
   ]
}
```