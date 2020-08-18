
# 迁移环境安装部署
[filename](../vmdeploy.md ':include')

# 云端数据代理 - HyperGate

## 创建云端数据代理

1. 登录阿里云‘管理控制台’，点击【云服务器ECS】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/8.png ':size=80%')

2. 点击【实例】→选择创建实例的地域→点击【创建实例】

![9.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/9.png ':size=80%')

3. 基础配置

![10.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/10.png ':size=80%')

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
镜像 | 自定义镜像，选择镜像源（名称为HM_IMG_<date>.qcow2）
系统盘 | 高效云盘 建议100G，最低40G

!> 注：如未上传镜像源请参考文档中的导入自定义镜像上传自定义镜像，或联络我们的实施工程师获取共享镜像

4. 填写完成后点击【下一步，网络和安全组】

5. 网络和安全组配置

![11.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/11.png ':size=80%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
网络   | 选择创建安全组的同一VPC网络，任意可用交换机
公网带宽| 勾选‘分配公网IPv4地址’，选择‘按使用流量’
带宽 | 选择‘5M’
安全组    | 选择开放12222/18090/3260/22端口号的安全组

6. 选择完成后点击【下一步，系统配置】

![12.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/12.png" ':size=80%')

?> 配置内容填写参考：

选项  | 选项填写
-----------------| -------------
登录凭证| 自定义密码
实例名称| HyperGate
主机名 | HyperGate

7. 选择完成后点击【下一步，确认订单】

检查创建信息，勾选《云服务器ECS服务条款》，点击【创建实例】,

![13.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/13.png" ':size=80%')

8. 创建成功

提示'创建成功'，选择【管理控制台】,

![14.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/14.png" ':size=80%')

9. 查看IP信息并记录

![15.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/15.png" ':size=80%')

---

## 配置ECS实例密码

1. 在实例列表中，点击创建实例的【远程连接】按钮

![16.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/16.png" ':size=80%')

2. 点击【修改远程连接密码】，进入修改密码后确认

![17.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/17.png" ':size=80%')

3. 进入修改密码后确认

![18.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/18.png" ':size=80%')

4. 密码修改完成后在密码输入框中输入上步所设定的密码。

## 选择安装角色

1. 登录后自动进入安装界面，光标选择到'HyperGate'，'Enter'键入

![19.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/19.png" ':size=80%')

2. 系统自动部署完成

![20.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/20.png" ':size=80%')

---

## 创建HyperDoor镜像

1. 重启所创建实例，使数据落盘;

2. 管理控制台界面，选择【云服务器ECS】-【实例】

3. 在实例列表中，点击创建实例的【更多】-【磁盘和镜像】-【创建自定义镜像】

![21.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/21.png" ':size=80%')

4. 填写自定义镜像名称、自定义镜像描述，默认资源组，并选择【创建】

![22.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/22.png" ':size=80%')

5. 管理控制台页面，选择【云服务器ECS】-【镜像】，记录该镜像ID

![23.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/standalone/aliyun/23.png" ':size=80%')
