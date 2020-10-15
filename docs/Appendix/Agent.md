---




### 3.1 Windows Agent安装说明


**1. 登录Windows主机并安装可执行文件（源端本地）**


!> 注：除Windows 2003 x86版本默认安装路径不同，其他版本安装过程无差异。</br>

?> 用户须在管理员模式下安装**Windows-Agent-Installer.exe文件**。</br>


打开安装界面，如下图（默认安装路径为“C:\Program Files\Windows-Agent”）点击【下一步】，按引导步骤安装

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image043.png ':size=40%') &ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image044.png ':size=40%')

!> 注：安装过程中，不同的安装包会根据不同的系统安装依赖程序，Windows 2008以下的版本没有自带Microsoft Initiator程序，会同其他依赖程序一并进行安装。</br>


![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image045.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image046.png ':size=40%')

安装完成后，点击【完成】，并根据提示重启主机.

!>注：1. 安装完成后，会在所选安装目录的同级目录生成一个“Windows-Agent”文件夹，此文件夹为程序运行目录，运行生成的相关日志也保存在此文件夹中;</br>
 &ensp;&ensp;&ensp; 2. 安装完成后，需重启主机已保障Windows agent的正常运行。



**2. 初始化ISCSI服务（源端本地）**

【控制面板】→【系统和安全】→【管理工具】→运行iSCSI Initiator程序

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image047.png ':size=50%')


**3. 配置防火墙（源端本地）**


?>请根据实际需要在以下两种环境中选择配置：</br>


**<font face="中易宋体" size=4 color=blue>&ensp; • Windows 2008/2012/2016</font>**

打开【Windows防火墙】，将Windows-Agent.exe服务加入防火墙允许服务，根据版本不同，设置方式略有差异，详见下图所示：

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image048.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image049.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image050.png ':size=38%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image051.png ':size=45%')

!>注：默认路径：C:\Users\Administrator\AppData\Local\Microsoft\Windows

**<font face="中易宋体" size=4 color=blue>&ensp; • Windows 2003</font>**

打开Windows防火墙，依次点击【例外】→【添加程序】→【浏览】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image052.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image053.png ':size=40%')

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image054.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image055.png ':size=40%')

选中Windows-Agent.exe程序，点击【打开】；
在“添加程序”列表可看到“Windows-Agent.exe”默认被选中，点击【确定】完成添加，并重启系统。

!>注：1. 非app.exe程序;</br>
  &ensp;&ensp;&ensp;&ensp;2. 目录默认为“C:\Program Files (x86)\Windows-Agent\ Windows-Agent.exe”，</br>
  &ensp;&ensp;&ensp;&ensp;2003 X86为“C:\Program Files\ Windows-Agent\ Windows-Agent.exe。</br>



**4. 运行程序（源端本地）**

安装、配置防火墙并重启后，点击桌面【Windows-agent】将其运行；

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image056.png ':size=10%')

?> 按以下格式要求填写：</br>
&ensp;&ensp;&ensp;HyperMotion访问地址：http://:HyperMotionIP:18766； </br>
&ensp;&ensp;&ensp;NAT地址：填写本地NAT地址（纯IP地址），若为空，则会默认使用本机IP作为参数，点击【启动】；

系统自动弹出 “Windows Agent正常启动”对话框，点击【是】

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image057.png ':size=40%')&ensp;&ensp;&ensp;
![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image058.png ':size=40%')

!>注：1.Windows Agent服务开始运行并注册到所选HyperMotion平台。此时，Windows Agent服务在后台运行，关闭Agent界面不会对服务有影响，如机器重启Windows Agent服务会自动启动；
 &ensp;&ensp;&ensp;2. Windows Agent服务启动后，可在HyperMotion主控台中看该注册的主机，请返回HyperMotion主控台查看并继续其他操作。
 
 ---
 
### 3.2 Linux Agent安装说明

**1. 执行下列命令自动完成安装**

```
#curl http://<HyperMotio的IP地址:10080>/softwares/getplusagent.sh | bash
```

**2. 执行以下命令查看Agent状态：**

```  
# egisplus-cli agent check
```

![8.png](https://oneprocloud.oss-cn-beijing.aliyuncs.com/_images/agent/image059.png ':size=60%')

**3. Agent安装成功后，Agent service和iSCSI service已启动，并且Agent也已自动注册，等待执行保护操作。**

!>注：Linux Agent服务启动后，可在HyperMotion主控台中看该注册的主机，请返回HyperMotion主控台查看并继续其他操作。



