
# <font face="方正正黑简体" size=5 >**一、概述**  </font> 

<font face="方正正黑简体" size=5>&ensp;&ensp;HyperMotion SaaS是一款在线云迁移软件，
&ensp;&ensp;在保证业务系统连续性的基础上，                         
&ensp;&ensp;可将物理服务器或虚拟机迁移至云平台，或云平台之间互相迁移，
&ensp;&ensp;目前支持源端 VMware到目标端 AWS、阿里云、华为云、腾讯云的迁移，
</font>


# <font face="方正正黑简体" size=5 >**二、功能介绍**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;迁移软件系统由两大模块组成: HyperMotion控制台和HyperGate组件。
&ensp;&ensp;- **HyperMotion控制台**为迁移主控台角色，负责迁移程序操作及流程控制，为SaaS端部署平台，通过URL地址可直接访问；                      
&ensp;&ensp;- **HyperGate组件**提供迁移数据同步及迁移流转自动适配目标平台功能，需布署在目标云主机(阿里云实例)。                        
</font>

# <font face="方正正黑简体" size=5 >**三、步骤索引**  </font>
![索引列表](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/1.png)

# <font face="方正正黑简体" size=5 >**四、账号注册**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;我们的客服人员会向您发送注册的邮件邀请，点击‘注册账号’按钮，</font>
![账号注册](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/2.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;进入系统注册界面，</font>
![账号注册2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/3.png)
<font face="方正正黑简体" size=3>&ensp;&ensp;*注：1. 发送连接邮箱地址：hypermotion@oneprocloud.com；*                               
&ensp;&ensp;&ensp;&ensp;&ensp;*2. 密码需设置为6-20个字符且必须包含字母和数字，支持特殊字符；*
&ensp;&ensp;&ensp;&ensp;&ensp;*3. 如果有问题，请及时联系您的企业管理员。*
</font>

# <font face="方正正黑简体" size=5 >**五、登陆访问**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;注册完成后，系统会自动跳转至登陆界面，
&ensp;&ensp;如未跳转，请直接访问：https://office.oneprocloud.com:8888/
&ensp;&ensp;推荐使用谷歌浏览器。
</font>
![login](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/4.png)

# <font face="方正正黑简体" size=5 >**六、概览视图**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;登录后，系统进入概览页面，</font>
![概览界面](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/5.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;建议步骤：【1.license授权区】获取授权→【2.源端连接设置区】连接源端VWware平台→【3.目标端连接设置区】连接目标端云平台→【4.迁移向导区】开始迁移。</font>

# <font face="方正正黑简体" size=5 >**七、获取授权**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;【运营管理】→【商品管理】，
&ensp;&ensp;勾选您所要购买的License授权商品，点击‘立即购买’，
</font>
![获取授权](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/6.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;确认购买，点击‘提交订单’
</font>
![获取授权2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/7.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;购买成功后系统提示‘购买成功，同时可在【设置】→【授权】中查看已授权信息。
</font>

# <font face="方正正黑简体" size=5 >**八、源端连接设置**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;返回概览界面，点击迁移向导中的‘选择主机’步骤，进入源端连接设置界面，
</font>
![获取授权源端连接12](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/8.png)
<font face="方正正黑简体" size=5>&ensp;**1. 下载和安装同步节点**
&ensp;&ensp;a. 点击下载链接，系统会自动将OVA文件下载至本地
</font>
![源端连接2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/9.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;b. 登陆VMware vCenter控制台，上传OVA文件，完成OVF模板部署，
</font>
<font face="方正正黑简体" size=3>&ensp;&ensp;*注：部署方式请参照VMware文档中[部署OVF模板]([链接地址](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html)) 的说明。*
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;c. 登陆通过OVA导入的主机（用户名root，密码onepro），复制命令并执行:
</font>
![源端连接3](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/10.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;安装完成后点击【下一步】按钮，
</font>
<font face="方正正黑简体" size=5>&ensp;**2. 创建VWware连接**
</font>
![源端连接4](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/11.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;需要填写的信息说明
</font>
字段  | 含义
------------- | -------------
vCenter IP 地址  | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码
同步节点 | 通过OVA导入的主机IP
<font face="方正正黑简体" size=5>&ensp;&ensp;填写完成后点击【下一步】按钮，
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;d. 源端连接完成，可在【设置】→【源端平台设置】中查看连接情况。
</font>


# <font face="方正正黑简体" size=5 >**九、目标端连接设置**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;返回概览界面，点击目标云平台连接中的‘阿里云’图标，
</font>
![目标端1](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/12.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;进入目标端连接界面,根据安装步骤操作：
</font>
![目标端2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/13.png)
<font face="方正正黑简体" size=5>&ensp;**1.   安装部署HyperGate**
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;a. 创建一台实例，命名为**HyperGate**
</font>
<font face="方正正黑简体" size=3>&ensp;&ensp;*注：1. 此步骤操作请在目标端阿里云平台上进行操作*；
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;*2.部署方式请参照VMware文档中[部署OVF模板]([链接地址](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html)) 的说明。*
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;b. 登陆<HyperGate>实例主机，复制并执行以下命令:
&ensp;&ensp;&ensp;`~]# curl https://download.oneprocloud.com/softwares/getdocker.sh |sudo bash`
</font>
![目标端3](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/14.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;c.复制并执行以下命令，完成部署：
&ensp;&ensp;&ensp;`~]#curl https://download.oneprocloud.com/softwares/gethypergate.sh |sudo bash`
</font>
![目标端4](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/15.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;安装阶段步骤完成后点击【下一步】按钮，
</font>
<font face="方正正黑简体" size=5>&ensp;**2.   填写云平台认证信息**
</font>
![目标端5](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/16.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;需要填写的信息说明
</font>
字段  | 含义
------------- | ----------------------
云平台服务注册地址  | 云平台已安装HyperGate的虚机IP地址，需与HyperMotion与阿里云互通
云平台服务端口  | 默认的服务端口为18090
Access Key ID | 阿里云的个人账户密钥ID  (详情参见附录二 阿里云平台认证信息获取)
AccessKeySecret  | 阿里云的个人账户密钥(详情参见 附录二 阿里云平台认证信息获取)
API接入地址 | 默认 ecs.aliyuncs.com
<font face="方正正黑简体" size=5>&ensp;**3.   填写云平台认证信息**
</font>
![目标端6](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/17.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;需要填写的信息说明
</font>
字段  | 含义
------------- | ----------------------
地域ID  |选择安装HyperGate虚机所在地域（例：华北、华东、香港）
可用区ID  | 选择安装HyperGate虚机所在区域 （如华北1可用区B  华北1 可用区C）
镜像ID | 创建的阿里云的镜像ID（详情参见附录二 阿里云平台认证信息获取）
<font face="方正正黑简体" size=5>&ensp;&ensp;填写完成后点击【完成】按钮，系统提示‘创建目标端存储成功’，
&ensp;&ensp;同时可在【设置】→【目标平台设置】中查看连接情况。
</font>
![目标端7](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/18.png)

# <font face="方正正黑简体" size=5 >**十、迁移向导**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;返回概览界面，点击迁移向导中的‘选择主机’步骤，进入迁移向导界面，
</font>
![迁移1](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/19.png)
<font face="方正正黑简体" size=5>&ensp;**1.   选择待迁移主机**
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;a. 进入迁移向导界面后，选择【添加主机】，
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/20.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;b. 选择【源端类型】，选择‘VMware’，
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/21.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;c. 列表中自动列出vCenter平台连接下的全部虚拟机，勾选需迁移的虚机后，点击【确认】，
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/22.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;d. 系统跳转回‘选择主机’界面，选择添加的待迁移虚机，点击下一步
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/23.png)

<font face="方正正黑简体" size=5>&ensp;**2.   数据拷贝**
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;a. 选择已经设定的一个存储设备连接，点击【确定】
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/24.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;b. 同步数据，在跳出“同步数据”对话框中点击【确定】，
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/25.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;c. 等待数据同步完成，完成继续点击下一步
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/26.png)
<font face="方正正黑简体" size=5>&ensp;**3.  开始迁移并完成迁移**
</font>
<font face="方正正黑简体" size=5>&ensp;&ensp;a. 选择待迁移主机，点击启动主机
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/27.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;b. 系统自动跳出提示框，选择确认无误后点击【确定】
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/28.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;c. 系统提示‘开始启动主机’，等待启动主机，系统提示‘启动系统完成’
</font>
![迁移2](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/29.png)
<font face="方正正黑简体" size=3>&ensp;&ensp;*注：待迁移主机将在目标平台上创建。请到HyperGate所在租户查看资源。*
</font>

# <font face="方正正黑简体" size=5 >**十一、资源清理**  </font> 
<font face="方正正黑简体" size=5>&ensp;&ensp;a. 选择已迁移完成的主机，点击【资源清理】
</font>
![资源1](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/30.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;b.  系统自动弹出‘资源清理’，勾选‘强制清理’，点击【确定】
</font>
![资源1](https://github.com/oneprocloud/hypermotion_docs/raw/master/images/image_hm_saas/31.png)
<font face="方正正黑简体" size=5>&ensp;&ensp;c.  清理成功后，可在【已清理】界面查看已迁主机的具体地址。
</font>