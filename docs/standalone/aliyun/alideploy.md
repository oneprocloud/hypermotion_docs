

---
## 1. 创建实例，命名为 HyperGate

!> 注：1. 此步骤操作请在目标端阿里云上进行操作；</br>
 &ensp; &ensp; &ensp;2. 请使用上传的[自定义镜像]（http://127.0.0.1:3000/#/standalone/aliyun/premise）（名称为HM_IMG_.qcow2）创建实例；
 &ensp; &ensp; &ensp;3. 部署方式及参数要求请参照[ 附录 创建HyperGate实例](https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vsphere.vm_admin.doc_50%2FGUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html) 的说明。
 

---

## 2. 自动进入安装部署界面

**1. 登录后自动进入安装界面，光标选择到'HyperGate'，'Enter'键入**

![19.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/19.png" ':size=70%')

**2. 系统自动部署完成**

![20.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/20.png" ':size=70%')

---

## 3. 创建HyperDoor镜像

**1. 重启所创建实例，使数据落盘;**

**2. 管理控制台界面，选择【云服务器ECS】-【实例】**

**3. 在实例列表中，点击创建实例的【更多】-【磁盘和镜像】-【创建自定义镜像】**

![21.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/21.png" ':size=90%')

**4. 填写自定义镜像名称、自定义镜像描述，默认资源组，并选择【创建】**

![22.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/22.png" ':size=60%')

**5. 管理控制台页面，选择【云服务器ECS】-【镜像】，记录该镜像ID**

![23.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/23.png" ':size=90%')
