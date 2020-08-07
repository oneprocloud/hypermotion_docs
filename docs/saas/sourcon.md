## 源端连接设置

返回概览界面，点击迁移向导中的【选择主机】步骤，进入源端连接设置界面

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/8.png ':size=80%')

## 下载和安装同步节点
1. 点击下载链接，系统会自动将OVA文件下载至本地

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/9.png ':size=80%')

2. 登陆VMware vCenter控制台，上传OVA文件，完成OVF模板部署，

!> 注：部署方式请参照VMware文档中[部署OVF模板](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html) 的说明。

3. 登陆通过OVA导入的主机（用户名root，密码onepro），复制命令并执行:

![10.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/10.png ':size=80%')

4. 安装完成后点击【下一步】按钮。

## 创建VWware连接

1. 添加源端VMwar连接

![11.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/11.png ':size=80%')

?> 需要填写源端VMware连接信息说明所示，请按照提示填写

字段  | 含义
------------- | -------------
vCenter IP 地址  | vCenter或ESXi地址，例：192.168.10.4
vCenter IP 地址端口  | 默认为443
vCenter账户  | vCenter或ESXi的用户名
vCenter账户密码  | vCenter或ESXi的密码
同步节点 | 通过OVA导入的主机IP

填写完成后点击【下一步】按钮

2. 源端连接完成，可在【设置】→【源端平台设置】中查看连接情况。