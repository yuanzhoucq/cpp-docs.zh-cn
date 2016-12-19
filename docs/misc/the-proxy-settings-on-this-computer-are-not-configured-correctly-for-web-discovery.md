---
title: "此计算机上的代理设置没有正确地针对 Web 发现进行配置。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_MUSTSPECIFYPROXYSERVER"
  - "vs.WebDiscoveryProxyHelp"
ms.assetid: aea2cc20-9180-47cb-b1ed-78fa5f8a407f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 此计算机上的代理设置没有正确地针对 Web 发现进行配置。
如果在位于防火墙后面的计算机上进行开发，并且尚未显式指定 Internet Explorer 连接的代理服务器，则在“添加 Web 引用”对话框中会出现此错误。 你需要在网络上显式指定代理服务器的地址和端口，以使防火墙外的服务对“添加 Web 引用”对话框中的 Web 浏览器可用。 .NET Framework 忽略 Internet Explorer 连接的自动检测代理选项。 可能需要询问网络管理员以获取该代理信息。  
  
 有关“防火墙和 Web 代理客户端的自动发现”的详细信息，请参阅 [http:\/\/www.microsoft.com\/technet\/prodtechnol\/isa\/2004\/plan\/automaticdiscovery.mspx](http://www.microsoft.com/technet/prodtechnol/isa/2004/plan/automaticdiscovery.mspx)  
  
### 指定 Internet Explorer 的代理服务器  
  
1.  在“工具”菜单上，选择“选项”。  
  
2.  在“选项”对话框中，选择“环境”，然后选择“Web 浏览器”。  
  
3.  单击“Internet Explorer 选项”。  
  
4.  在“连接”选项卡上，单击“LAN 设置”。  
  
5.  取消选择“自动检测设置”。  
  
6.  在“代理服务器”区域，选择“为 LAN 使用代理服务器\(这些设置不会应用于拨号或 VPN 连接\)”。  
  
7.  指定符合你的网络的地址和端口号。  
  
8.  单击“确定”，单击“确定”，然后再次单击“确定”。  
  
9. 在“文件”菜单上，选择“退出”，然后重新打开 Visual Studio。  
  
## 请参阅  
 [NIB：“添加 Web 引用”对话框](http://msdn.microsoft.com/zh-cn/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [NIB：如何添加和删除 Web 引用](http://msdn.microsoft.com/zh-cn/a7ddaa5d-4672-405b-91b3-39de65d7e3a2)   
 [Programming the Web with XML Web Services](http://msdn.microsoft.com/zh-cn/2d651a26-73df-4b39-85fa-7913a7d6bee4)