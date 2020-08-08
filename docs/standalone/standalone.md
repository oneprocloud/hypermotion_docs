# 《HyperMotion 单机版本》产品概述

---

**「HyperMotion 单机版本」**主要适用于私有化环境本地部署，有些环境并非可以互联网应用，有相关安全政策要求，单机版本可以更加的安全、可靠的进行数据迁移工作<br/>
该文档主要阐述HyperMotion单机版迁移产品进行云迁移的安装及具体操作流程

## **功能概述**

迁移软件系统由两大模块组成: **「HyperMotion>控制台」**和 **「HyperGate>云端数据代理」**<br/>

**「HyperMotion>控制台」** 为迁移主控平台角色，负责迁移程序调度以及流程控制<br/>
**「HyperGate>云端数据代理」** 提供迁移目标数据接收代理同步及驱动自动适配目标平台功能，此组件必须部署在迁移的目标云平台（HyperGate在目标源端体现为一台云主机，在其内部安装云端数据代理程序）<br/>

## 文档目录

!> **请根据您所要迁移的目标云平台选择阅读以下安装及操作指南:**

- [阿里云](standalone/aliyun/aliyun.md)
 - [迁移流程动画](standalone/aliyun/migrpro.md)
 - [前提准备](standalone/aliyun/premise.md)
 - [迁移安装部署](standalone/aliyun/alideploy.md)
 - [迁移操作使用](standalone/aliyun/alioper.md)
- [腾讯](standalone/tencent/tencent.md)
- [华为](standalone/huawei/huawei.md)
- [AWS](standalone/aws/aws.md)