---
title: "OLE 后台：容器和服务器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, OLE 容器应用程序"
  - "完全服务器"
  - "OLE 容器, 容器应用程序"
  - "OLE 完全服务器应用程序"
  - "OLE 服务器应用程序, 关于服务器应用程序"
  - "OLE 服务器应用程序, 袖珍服务器应用程序"
  - "服务器应用程序"
  - "服务器应用程序, 与容器的通信"
  - "服务器应用程序, 已定义"
  - "服务器应用程序, 完全服务器与袖珍服务器"
  - "服务器应用程序, 要求"
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 后台：容器和服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

容器应用程序是可以合并嵌入或链接的项到它自己中文档的应用程序。  容器应用程序管理的文档必须能够存储和查看 OLE 文档组件和应用程序创建的数据。  容器应用程序必须也允许用户插入新项或通过激活服务器应用编辑现有项，则需要。  容器应用程序的用户界面在要求文章 [容器：用户界面问题](../mfc/containers-user-interface-issues.md)列出。  
  
 服务器应用程序或组件的应用程序可供组件创建 OLE 文档容器应用程序使用的应用程序。  通常服务器应用支持拖放或复制它们的对剪贴板的数据容器，以便应用程序可以将数据作为嵌入式或链接的项。  应用程序可以是容器和服务器。  
  
 多数服务器是独立应用程序或整个服务器；运行它们用作独立应用程序或可以由容器应用程序开始。  miniserver 是容器启动服务器应用程序的一个特定类型。  不能以独立应用程序。  Microsoft Draw 和 Microsoft 的服务器是 miniservers 的示例。  
  
 容器和服务器不直接通信。  相反，它们通过 OLE 系统动态链接库 \(DLL\) \(DLL\) 进行通信。  这些 DLL 函数提供容器和服务器调用和容器和服务器提供 DLL 调用的回调函数。  
  
 使用此通信方法，容器不需要知道服务器应用程序的实现详细信息。  容器允许它接受任何服务器创建的项，无需定义使用它可以服务器的类型。  结果，容器应用程序的用户都可以利用未来的应用程序和数据格式。  如果这些新应用程序是 OLE 组件，则复合文档可以合并这些应用程序创建的项。  
  
## 请参阅  
 [OLE 后台](../mfc/ole-background.md)   
 [OLE 后台：MFC 实现](../mfc/ole-background-mfc-implementation.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)   
 [容器：客户端项](../mfc/containers-client-items.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)