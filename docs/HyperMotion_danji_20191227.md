
# <font face="方正正黑简体" size=6 >**  **  </font>  

## <font face="方正正黑简体" size=6 >**概述**  </font>  
___  
### <font face="方正正黑简体" size=5 >**产品概述**  </font> 

</br><font face="中易宋体" size=3>HyperMotion云迁移在保证业务系统连续性的基础上，
</font>
</br><font face="中易宋体" size=3>可将物理服务器或虚拟机迁移至云平台，或云平台之间互相迁移，
</font>
</br><font face="中易宋体" size=3>该文档主要阐述使用HyperMotion迁移产品进行云迁移的安装及具体操作流程。
</font>
</br><font face="中易宋体" size=3>更多权限申请及迁移咨询：enquiry@oneprocloud.com。
</font>
</br>
 ---
### <font face="方正正黑简体" size=5 >**功能介绍**  </font> 

<font face="中易宋体" size=3>迁移软件系统由两大模块组成: HyperMotion控制台和HyperGate组件。
</br>• <**HyperMotion控制台**>为迁移主控台角色，负责迁移程序操作及流程控制，建议部署在源端主机；
</br>• <**HyperGate组件**>提供迁移数据同步及迁移流转自动适配目标平台功能，需布署在目标云主机。                        
</font>
 ***
### <font face="方正正黑简体" size=6 >**支持列表**  </font>  
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/26.png" width="1000">
___

### <font face="方正正黑简体" size=5 >**步骤索引**  </font>
<font face="中易宋体" size=4> &ensp;[**安装步骤：**](about.md)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;1. &ensp;[账号注册](#账号注册)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;2. &ensp;[登陆访问](#登陆访问)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;3. &ensp;[概览视图](#概览视图)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;4. &ensp;[获取授权](#获取授权)
</font>
</br>
</br>
<font face="中易宋体" size=4> &ensp;[**操作步骤：**](about.md)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;5. &ensp;[源端连接](#源端连接)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;6. &ensp;[目标端连接](#目标端连接)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;7. &ensp;[迁移向导](#迁移向导)
</font>
</br>
<font face="中易宋体" size=3>&ensp;&ensp;&ensp;8. &ensp;[资源清理](#资源清理)
</font>
</br>
___

## <font face="方正正黑简体" size=6 >**安装指南**  </font>  
<font face="中易宋体" size=3 >您获取到的镜像包格式如下：
</font>
</br>
___
### <font face="方正正黑简体" size=5 >**获取镜像包**  </font> 
<font face="中易宋体" size=3>您获取到的镜像包格式如下：
</font>
</br>
</br><font face="中易宋体" size=3 color="#000066">•  **如安装环境为VMware虚拟机：**
</font>
</br><font face="中易宋体" size=3>&ensp;获取的镜像包名称为：HyperMotion-latest-<date>-full.iso；
</font>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/1.png" width="500">
</br>
</br><font face="中易宋体" size=3 color="#000066">•  **如安装环境为云平台实例：**
</font>
</br><font face="中易宋体" size=3>&ensp;获取的镜像包名称为：HM_IMG_<date>.qcow2
</font>
</br>
&ensp;<img src="https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_danji/2.png" width="350">
</br>
 ---

### <font face="方正正黑简体" size=5 >**环境准备及确认（目标平台）**  </font> 
___
#### <font face="方正正黑简体" size=4 color=blue>**阿里云**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**AWS**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**Azure**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**OpenStack**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**OpenStackImageBootV2**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**腾讯云**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**青云**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**天翼云**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**UCloud**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**ZStack**  </font> 
 ---
#### <font face="方正正黑简体" size=4 color=blue>**通用存储方式**  </font> 
  ---
  
### <font face="方正正黑简体" size=5 >**安装步骤一：HyperMotion控制台**  </font> 
  ---
<font face="中易宋体" size=3>**1.   将获取的镜像包上传至源端VMware平台或源端云平台**
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
### <font face="方正正黑简体" size=5 >**安装步骤二：HyperGate组件**  </font> 

## <font face="方正正黑简体" size=6 >**操作指南**  </font>  