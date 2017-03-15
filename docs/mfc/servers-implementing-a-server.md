---
title: "服务器：实现服务器 | Microsoft Docs"
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
  - "OLE 服务器应用程序, 实现 OLE 服务器"
  - "服务器, 实现"
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 服务器：实现服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明 MFC 应用程序向导为可视化编辑服务器应用创建的代码。  如果不使用应用程序向导，本文列表区域必须编写代码来实现服务器的应用场合。  
  
 如果使用应用程序向导创建新的服务器应用程序，它为您提供大量特定于服务器的代码。  如果向可视化编辑服务器功能中向现有应用程序，您必须复制应用程序向导在添加需要的服务器代码的其余部分之前提供的代码。  
  
 应用程序向导提供可分为若干类别的服务器代码：  
  
-   管理服务器资源  
  
    -   使用菜单资源编辑的，当服务器在其自己的窗口的嵌入项。  
  
    -   使用资源，当服务器可用的菜单和工具栏都准备就绪。  
  
     有关这些资源的更多信息，请参见 [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)。  
  
-   定义从 `COleServerItem`派生的项类。  有关服务器项的更多详细信息，请参见 [服务器：服务器项目](../mfc/servers-server-items.md)。  
  
-   文档更改类的基类为 `COleServerDoc`。  有关更多详细信息，请参见 [服务器：实现服务器文档。](../mfc/servers-implementing-server-documents.md)。  
  
-   定义从 `COleIPFrameWnd`派生的框架窗口类。  有关更多详细信息，请参见 [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)。  
  
-   创建服务器应用的项存储在 Windows 注册数据库和注册服务器的新实例。OLE 的系统。  有关本主题的更多信息，请参见 [](../mfc/registration.md "Registration")。  
  
-   初始化和启动服务器应用。  有关本主题的更多信息，请参见 [](../mfc/registration.md "Registration")。  
  
 有关更多信息，请参见 [COleServerItem](../mfc/reference/coleserveritem-class.md) 中[COleServerDoc](../mfc/reference/coleserverdoc-class.md) 和 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) in the *宏和全局*下的 RFX 函数。  
  
## 请参阅  
 [服务器](../mfc/servers.md)   
 [容器](../mfc/containers.md)   
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [注册](../mfc/registration.md)