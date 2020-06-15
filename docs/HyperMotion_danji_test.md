# 


## <font face="方正正黑简体" size=6 >** 概述** </font>  
</br><font face="中易宋体" size=3>该文档主要阐述使用HyperMotion迁移产品进行云迁移的安装及具体操作流程。
</font>
 ---
### <font face="方正正黑简体" size=5 >**功能概述** </font> 

<font face="中易宋体" size=3>迁移软件系统由两大模块组成: HyperMotion控制台和HyperGate云端数据代理。
</br>• <**HyperMotion>控制台**为迁移主控台角色，负责迁移程序操作及流程控制；
</br>• <**HyperGate>云端数据代理**提供迁移数据同步及迁移流转自动适配目标平台功能，需布署在目标云主机。                        
</font>
 ---
</br>请根据您所要迁移的目标云平台选择阅读以下安装及操作指南：
</font>
 ***
## <font face="方正正黑简体" size=6 >** 阿里云（公有云）**  </font>  
___

### <font face="方正正黑简体" size=5 >** 迁移流程图（动画）**  </font> 

<video src="https://oneprocloud.oss-cn-beijing.aliyuncs.com/donghua.mp4" width="600px" height="400px" controls="controls" loop="loop"></video>


___

### <font face="方正正黑简体" size=5 >** 安装包下载**  </font> 
<font face="中易宋体" size=3>请获取以下安装包并上传至指定平台：
</font>
</br>
<font face="中易宋体" size=3>**1.HyperMotion控制台**
</font>
</br>

- VMware平台安装
【*注释：如果迁移源端为VMware平台，则必须部署在源端*】</br>
<a href="http://office.oneprocloud.com:18888/iso/hypermotion/haitong/HyperMotion-191227-20200224-full.iso" download="HyperMotion-V3-full.iso">HyperMotion ISO包下载</a><br>

- 云端安装<br>
<a href="http://office.oneprocloud.com:18888/iso/hypermotion/%e6%9d%ad%e5%b7%9e%e6%94%bf%e5%8a%a1%e4%ba%91/HM_IMG-191227-2020-03-19.raw" download="HyperMotion-V3-full.raw">HyperMotion RAW镜像下载</a>

<font face="中易宋体" size=3>**2.Hypergate云端数据代理**
</font>

此组件需要部署在迁移的目标云平台</br>

- 下载链接</br>
<a href="http://office.oneprocloud.com:18888/iso/hypermotion/%e6%9d%ad%e5%b7%9e%e6%94%bf%e5%8a%a1%e4%ba%91/HM_IMG-191227-2020-03-19.raw" download="HyperMotion-V3-full.raw">HyperMotion RAW镜像下载</a>
 ***
### <font face="方正正黑简体" size=5 >** 安装指南** </font> 
___
####<font face="方正正黑简体" size=4 color=blue>**步骤一：HyperMotion控制台**  </font> 
  ---
<font face="中易宋体" size=3>**1.   将获取的镜像包上传至源端VMware平台或云平台**
</font>
</br>
<font face="中易宋体" size=3>** 2.    在源端创建一个虚机或实例，命名为HyperMotion**
</font>
</br><font face="中易宋体" size=3>&ensp;虚机或实例配置要求如下：
</font>
</br>

字段  | 含义
------------- | -------------
vCenter IP 地址  | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码
同步节点 | 通过OVA导入的主机IP

</br>

<font face="中易宋体" size=3>**3.  登陆虚机或实例控制台，首次登陆修改密码**
</font>
</br><font face="中易宋体" size=3>&ensp;登录名：<u>operator</u>
</font>
</br><font face="中易宋体" size=3>&ensp;登录密码：<u>P@ssw0rd</u>
</font>
</br>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/3.png" width="600">
</br>
</br>
<font face="中易宋体" size=3>**4.  设置网络（仅VMware平台虚机需要配置此步骤）**
</font>
</br><font face="中易宋体" size=3>&ensp;根据实际情况填写框内信息，‘Enter’键入下一步，
</font>
</br>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/4.png" width="300">
</br>

<font face="中易宋体" size=3>**5.  自动进入安装部署界面**
</font>
</br>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/5.png" width="280">
</br>
</br>
<font face="中易宋体" size=3>**6.  系统自动部署完成**
</font>
</br>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/7.png" width="500">
</br>
</br>
 ---
####<font face="方正正黑简体" size=4 color=blue>**步骤二：HyperGate云端数据代理**  </font> 
<font face="中易宋体" size=3>**1. 创建实例，命名为 HyperGate **
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;登录阿里云‘管理控制台’，点击【云服务器ECS】
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/8.png" width="650>

</br></br>
<font face="中易宋体" size=3>
</br>
</br><font face="中易宋体" size=3>&ensp;&ensp;点击【实例】→选择创建实例的地域→点击【创建实例】
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/9.png" width="650>
</br>
<font face="中易宋体" size=3>
</br></br>
<font face="中易宋体" size=3> &ensp;&ensp;基础配置：
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/10.png" width="650>
</br></br>

<font face="中易宋体" size=3> 
</font>
</br>

<font face="中易宋体" size=3>**2. 打开实例控制台，修改密码 **
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/10.png" width="650>
</br></br>
<font face="中易宋体" size=3> 
</font>
</br>
<font face="中易宋体" size=3>**3.  自动进入安装部署界面**
</font>
</br></br>
<font face="中易宋体" size=3>**4.  创建HyperDoor镜像**
</font>
___

### <font face="方正正黑简体" size=5 >** 网络策略开通** </font> 
___

### <font face="方正正黑简体" size=5 >** 使用指南** </font> 
___

####<font face="方正正黑简体" size=4 color=blue>**登录访问**</font> 
<font face="中易宋体" size=3>支持以下浏览器：Chrome(谷歌)，Firefox（火狐），Safari，
</font>
</br>
<font face="中易宋体" size=3>访问地址：http://< HyperMotion IP>:18088
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/27.png" width="650>
</br></br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;&ensp;用户名：<u>admin</u> &ensp;&ensp; 初始密码：<u>admin_pass</u>
</font>
<font face="中易宋体" size=2></br>&ensp;&ensp;*注：1. HyperMotion IP即创建HyperMotion虚机时的IP；                           
&ensp;&ensp;&ensp;&ensp;&ensp;*2. http://<HyperMotion IP>:18088中的“：”为英文格式；
</font>
 ---
 

####<font face="方正正黑简体" size=4 color=blue>**配置向导**</font>
 ---
 <font face="中易宋体" size=3>**1. 服务健康检查**
</font>
</br>
<font face="中易宋体" size=3>&ensp;登陆后，系统自动跳转至‘配置向导’服务健康检查界面，自动检测服务健康状况，确认服务健康状况均正常，点击【下一步】
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/28.png" width="650>
</br></br>
<font face="中易宋体" size=3> 
</font>
</br></br>
 ---
 <font face="中易宋体" size=3>**2. 激活License**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;阅读激活说明，确认后根据实际需要在以下两种方式中任选一种进行激活：
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/29.png" width="650>
<font face="中易宋体" size=3> 
</font>
</br></br>

<font face="中易宋体" size=3 color=blue>&ensp;•  **方式一：**扫描二维码（推荐）
</font>
</br>

<font face="中易宋体" size=3>&ensp;使用手机上的“微信”、“钉钉”、“支付宝”或带有扫描二维码的“浏览器”，扫描对话框中的二维码，并按要求填写相关信息
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/31.png" width="650>
<font face="中易宋体" size=3> 
</font>

<font face="中易宋体" size=2>&ensp;&ensp;*注：请正确填写公司名称、姓名、职位等信息，否则将无法收到序列号信息。                           
</font>
</br>
<font face="中易宋体" size=3>&ensp;扫描二维码方式提交成功后，激活码将以附件形式发送至所填写的邮箱中，请注意查收。收到激活码后粘贴到“激活码”框中，点击【激活】。
</font>
</br>

<font face="中易宋体" size=3 color=blue>&ensp;•  **方式二：**发送邮件
</font>
</br>

<font face="中易宋体" size=3>&ensp;点击【点击复制注册码】，将注册码以邮件形式发送至license@ oneprocloud.com
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/30.png" width="650>
<font face="中易宋体" size=3> 
</font>

<font face="中易宋体" size=2>&ensp;&ensp;*注：请正确填写公司名称、姓名、职位等信息，否则将无法收到序列号信息。                           
</font>

<font face="中易宋体" size=3>&ensp;邮件方式提交成功后，激活码将以附件形式发送至所填写的邮箱中，请注意查收。收到激活码后粘贴到“激活码”框中，点击【激活】
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/32.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;确认信息无误后点击【下一步】。
</font>
</br>

 ---
<font face="中易宋体" size=3>**3. 源端连接设置**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;请根据实际需要在以下四种连接方法中任选一种进行连接：
</font>
</br>

<font face="中易宋体" size=3 color=blue>&ensp;•  **方法一：无代理方式-连接VMware平台**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;选择VMware图标，自动跳转下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/33.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;填写vCenter相关信息后选择【下一步】，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/34.png" width="650>
<font face="中易宋体" size=3> 
</font>

<font face="中易宋体" size=3>&ensp;需要填写的信息说明
</font>

字段  | 含义
------------- | -------------
vCenter IP 地址&nbsp; &nbsp; &nbsp; &nbsp;    | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码

</br></br>
<font face="中易宋体" size=3>&ensp;系统提示’创建源端连接成功’，点击下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/35.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>


<font face="中易宋体" size=3 color=blue>&ensp;•  **方法二：无代理方式-连接OpenStack平台**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;选择OpenStack图标，自动跳转下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/36.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;填写OpenStack源平台信息后选择【下一步】，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/37.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>

<font face="中易宋体" size=3>&ensp;需要填写的信息说明
</font>

字段  | 含义
-----------------| -------------
云平台地址&nbsp; &nbsp; &nbsp; &nbsp;    | 例：http://192.168.11.201:5000/v3/
云平台域  | region（例：RegionOne、RG1、RG2）
租户组  | 项目组域名（默认为default）
云平台租户      | 租户、或项目名称、一般为登陆云平台的用户名(例：admin、xiaoming)
用户组  | 用户组域名 (默认为default)
云平台用户  | 登陆云平台的用户名
用户密码  | 登陆云平台的密码


</br></br>
<font face="中易宋体" size=3>&ensp;填写Ceph信息后选择【下一步】，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/38.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>

<font face="中易宋体" size=3>&ensp;需要填写的信息说明2
</font>

字段 | 含义
-----------------| -------------
Ceph控制节点地址&nbsp; &nbsp; &nbsp; &nbsp;   | ceph控制节点的地址  （例如：10.0.0.201） 需确认双方可以网络互通
Ceph集群 | 目前仅支持ceph
Ceph存储池  | ceph节点的存储池名称，默认为volumes
Ceph用户名     |ceph的用户名（例如：cinder、admin）
Ceph密匙环 | ceph的键值，在ceph控制节点cat /etc/ceph/ceph.client.admin.keyring查看

</br>
<font face="中易宋体" size=3>&ensp;系统提示’创建源端连接成功’，点击下一步。
</font>
</br></br>



<font face="中易宋体" size=3 color=blue>&ensp;•  **方法三：代理方式-连接windows主机**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;选择物理机机X86图标，自动跳转下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/39.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;点击选择所要获取的Agent安装包，进行下载，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/40.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;在待迁移物理机上安装Agent，
</font>
</br>
<font face="中易宋体" size=2>&ensp;*注：物理机端安装操作步骤可参考 附录一Windows Agent安装说明;*
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;所有对Agent的操作均在HyperMotion端触发，Windows Agent服务正常启动后，可在HyperMotion中看到注册的主机。
</font>
</br>
</br>

<font face="中易宋体" size=3 color=blue>&ensp;•  **方法四：代理方式-连接Linux主机**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;选择所要迁移Linux主机图标，自动跳转下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/41.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;点击选择所要获取的Agent安装包，进行下载，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/42.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;在待迁移Linux主机上安装Agent，
</font>
</br>
<font face="中易宋体" size=2>&ensp;*注：Liunx主机端安装操作步骤可参考 附录二 Linux  Agent安装说明；*
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;所有对Agent的操作均在HyperMotion端触发，linux  Agent服务正常启动后，可在HyperMotion中看到注册的主机。
</font>
</br>
 ---
 <font face="中易宋体" size=3>**4. 阿里云连接设置**
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;配置向导进入‘目标端平台配置’界面，选择阿里云图标，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/43.png" width="650>
</br></br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>&ensp;填写云平台认证信息后点击下一步，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/44.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3> 
</font>
<font face="中易宋体" size=3>&ensp;需要填写的信息说明
</font>

字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与阿里云互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录二 阿里云平台认证信息获取)
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录二 阿里云平台认证信息获取)
API接入地址 | 默认 ecs.aliyuncs.com

</br>

<font face="中易宋体" size=3>&ensp;需要填写的信息说明2
</font>

字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：华北、华东、香港）
可用区ID  | 选择安装HyperGate虚机所在区域 （如华北1可用区B  华北1 可用区C）
镜像ID | 创建的阿里云的镜像ID（详情参见附录二 阿里云平台认证信息获取）

</br>
 ---
 <font face="中易宋体" size=3>**5. 配置向导完成**
</font>
</br>

<font face="中易宋体" size=3>&ensp;目标平台配置信息填写完成后，点击【下一步】，确认配置信息无误后配置向导完成，系统提示修改密码后重新登录。
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/45.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
___
####<font face="方正正黑简体" size=4 color=blue>**迁移向导**</font>

<font face="中易宋体" size=3>&ensp;返回概览界面，点击迁移向导中的‘选择主机’步骤，进入迁移向导界面，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/46.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>**&ensp;1.   选择待迁移主机**
</font>
</br>
<font face="中易宋体" size=3>&ensp;a. 进入迁移向导界面后，选择【添加主机】，
</font>
</br></br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/48.png" width="650>
</br>
<font face="中易宋体" size=3> 
</font>
</br></br>
<font face="中易宋体" size=3>b. 选择【源端类型】，选择‘VMware’，
</font>
</br>
<font face="中易宋体" size=3> 
</font>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/49.png" width="650>
</br></br>
<font face="中易宋体" size=3>c. 列表中自动列出vCenter平台连接下的全部虚拟机，勾选需迁移的虚机后，点击【确认】，
</font>
</br>
<font face="中易宋体" size=3> 
</font>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/50png" width="650>
</br></br>
<font face="中易宋体" size=3>d. 系统跳转回‘选择主机’界面，选择添加的待迁移虚机，点击下一步
</font>
</br>
<font face="中易宋体" size=3> 
</font>
</br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/23.png" width="650">
</br></br>
<font face="中易宋体" size=3>**2.   数据拷贝**
</font>
<font face="中易宋体" size=3></br>a. 选择已经设定的一个存储设备连接，点击【确定】
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/24.png" width="650">
</br></br>
<font face="中易宋体" size=3>b. 同步数据，在跳出“同步数据”对话框中点击【确定】，
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/25.png" width="650">
</br>
<font face="中易宋体" size=3></br>c. 等待数据同步完成，完成继续点击下一步
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/26.png" width="650">
</br></br>
<font face="中易宋体" size=3>**3.  开始迁移并完成迁移**
</font>
<font face="中易宋体" size=3></br>a. 选择待迁移主机，点击启动主机
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/27.png" width="650">
</br></br>
<font face="中易宋体" size=3>b. 系统自动跳出提示框，选择确认无误后点击【确定】
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/28.png" width="650">
</br></br>
<font face="中易宋体" size=3>c. 系统提示‘开始启动主机’，等待启动主机，系统提示‘启动系统完成’
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/29.png" width="650">
</br>
<font face="中易宋体" size=2>&ensp;&ensp;*注：待迁移主机将在目标平台上创建。请到HyperGate所在租户查看资源。*
</font>
 ---

<font face="中易宋体" size=3>a. 选择已迁移完成的主机，点击【资源清理】
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/30.png" width="650">
</br></br>
<font face="中易宋体" size=3>b.  系统自动弹出‘资源清理’，勾选‘强制清理’，点击【确定】
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/31.png" width="650">
</br></br>
<font face="中易宋体" size=3>c.  清理成功后，可在【已清理】界面查看已迁主机的具体地址。
</font>
