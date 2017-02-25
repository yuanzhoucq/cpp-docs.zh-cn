---
title: "CAtlServiceModuleT::Run Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule::Run"
  - "CServiceModule.Run"
  - "CSecurityDescriptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 服务, 安全性"
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CAtlServiceModuleT::Run Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Run** 包含对的 `PreMessageLoop`、 `RunMessageLoop`和 `PostMessageLoop`。  在调用后，`PreMessageLoop` 首先存储服务的线程ID.  服务将使用此ID通过发送 **WM\_QUIT** 信息关闭它使用Win32 API函数，[PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)。  
  
 `PreMessageLoop` 然后调用 `InitializeSecurity`。  默认情况下，`InitializeSecurity` 调用与安全描述符的 [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) 设置为NULL，这意味着，任何用户可以访问对象的。  
  
 如果不希望服务指定自己的安全，重写 `PreMessageLoop`，并且不调用 `InitializeSecurity`，并且，COM将确定安全设置从注册表。  一种简便方式配置注册表设置与本节讨论后的 [DCOMCNFG](../atl/dcomcnfg.md) 实用工具。  
  
 click\-once安全指定，对象移至COM注册，以便新客户端可以连接到程序。  最后，程序调用这些服务控制管理器\(SCM\)运行它，并使用这些消息循环。  程序保持运行，直到宣告一出的消息在服务关闭。  
  
## 请参阅  
 [服务](../atl/atl-services.md)   
 [CSecurityDesc Class](../atl/reference/csecuritydesc-class.md)   
 [CSid Class](../atl/reference/csid-class.md)   
 [CDacl Class](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../Topic/CAtlServiceModuleT::Run.md)