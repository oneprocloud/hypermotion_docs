# 迁移向导

返回概览界面，点击迁移向导中的‘选择主机’步骤，进入迁移向导界面

![19.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/19.png ':size=80%')

## 选择待迁移主机

1. 进入迁移向导界面后，选择【添加主机】

![20.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/20.png ':size=80%')

2. 选择【源端类型】，选择‘VMware’

![21.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/21.png ':size=80%')

3. 列表中自动列出vCenter平台连接下的全部虚拟机，勾选需迁移的虚机后，点击【确认】

![22.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/22.png ':size=80%')

4. 系统跳转回‘选择主机’界面，选择添加的待迁移虚机，点击下一步

![23.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/23.png ':size=80%')

## 数据拷贝
1. 选择已经设定的一个存储设备连接，点击【确定】

![24.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/24.png ':size=80%')

2. 同步数据，在跳出“同步数据”对话框中点击【确定】

![25.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/25.png ':size=80%')

3. 等待数据同步完成，完成继续点击下一步

![26.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/26.png ':size=80%')

## 开始迁移并完成迁移

1. 选择待迁移主机，点击启动主机

![27.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/27.png ':size=80%')


2. 系统自动跳出提示框，选择确认无误后点击【确定】

![28.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/28.png ':size=80%')

3. 系统提示‘开始启动主机’，等待启动主机，系统提示‘启动系统完成’

![29.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/29.png ':size=80%')

!> 注：1.待迁移主机将在目标平台上创建。请到HyperGate所在租户查看资源

## 清理迁移资源

**请根据以下步骤提示清理：**

1. 选择已迁移完成的主机，点击【资源清理】

![30.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/30.png ':size=80%')

2. 系统自动弹出‘资源清理’，勾选‘强制清理’，点击【确定】

![31.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/saas/31.png ':size=80%')

3. 清理成功后，可在【已清理】界面查看已迁主机的具体地址。