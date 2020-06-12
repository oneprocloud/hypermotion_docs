# 


## <font face="方正正黑简体" size=6 >** 概述** </font>  
</br><font face="中易宋体" size=3>该文档主要阐述使用HyperMotion迁移产品进行云迁移的安装及具体操作流程。
</font>
 ---
### <font face="方正正黑简体" size=5 >**功能概述** </font> 

<font face="中易宋体" size=3>迁移软件系统由两大模块组成: HyperMotion控制台和HyperGate组件。
</br>• <**HyperMotion控制台**>为迁移主控台角色，负责迁移程序操作及流程控制；
</br>• <**HyperGate组件**>提供迁移数据同步及迁移流转自动适配目标平台功能，需布署在目标云主机。                        
</font>
 ---
</br>请根据您所要迁移的目标云平台选择阅读以下安装及操作指南：
</font>
 ***
## <font face="方正正黑简体" size=6 >** 阿里云（公有云）**  </font>  
___

### <font face="方正正黑简体" size=5 >** 迁移流程图（动画）**  </font> 
![在makrdown上生成gif动画](http://photocdn.sohu.com/20151125/mp44183873_1448421587734_7.gif)
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

<font face="中易宋体" size=3>**2.Hypergate组件**
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
</br><font face="中易宋体" size=3>&ensp;登录名：operator
</font>
</br><font face="中易宋体" size=3>&ensp;登录密码：P@ssw0rd
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
####<font face="方正正黑简体" size=4 color=blue>**步骤二：HyperGate组件**  </font> 
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
<font face="中易宋体" size=3>访问地址：http://<HyperMotion IP>:18088
</font>
</br></br>
<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/4.png" width="650">
</br>
 ---
 <p id="概览视图"></p>
___
####<font face="方正正黑简体" size=4 color=blue>**配置向导**</font> 
___
####<font face="方正正黑简体" size=4 color=blue>**迁移向导**</font>
___