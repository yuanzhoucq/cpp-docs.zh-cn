---
title: "CAtlServiceModuleT::Handler Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule::Handler"
  - "CServiceModule.Handler"
  - "Handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Handler method"
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::Handler Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CAtlServiceModuleT::Handler` 是服务控制管理器\(SCM\)调用检索服务的状态并为其提供不同的命令实例\(如停止或暂停\)。  SCM通过操作代码来 `Handler` 指示该服务应执行。  默认ATL生成了仅服务处理停机命令。  如果SCM通过停机命令，服务调用SCM程序将停止。  服务然后调用 `PostThreadMessage` 宣告一出的消息到它。  这将停止消息循环，而服务最终关闭。  
  
 处理多个命令，需要更改在 `CAtlServiceModuleT` 构造函数初始化的 `m_status` 数据成员。  此数据成员调用SCM启用服务时要使用的哪些按钮在服务控制面板应用程序选择。  
  
## 请参阅  
 [服务](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../Topic/CAtlServiceModuleT::Handler.md)