---
title: "MFC 中的 OLE | Microsoft Docs"
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
  - "应用程序 [OLE], 关于 OLE"
  - "MFC [C++], OLE 和"
  - "OLE [C++]"
  - "OLE 应用程序 [C++], 关于 OLE"
  - "OLE 组件对象模型 (COM)"
  - "OLE 容器, 关于 OLE"
  - "OLE 项"
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC 中的 OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些情景描述编程使用 MFC 的 OLE 的基本知识。  MFC 提供简便方法写入使用 OLE 的程序：  
  
-   使用 OLE 可视编辑对象 （就地激活）。  
  
-   作为工作 OLE 容器或服务器。  
  
-   实现拖放功能。  
  
-   使用日期和时间数据时使用。  
  
-   管理 MFC 模块的状态数据，包括导出的 DLL 函数入口点，OLE\/COM 接口入口点和窗口过程的入口点。  
  
 还可以使用 [自动化 \(U\)](../mfc/automation.md) 或从 [远程的自动化](../mfc/remote-automation.md) 程序运行其他程序。  
  
> [!NOTE]
>  OLE 术语表示技术与链接和 OLE 嵌入，包括容器、OLE 服务器、OLE 项、编辑 \(或就地激活的可视化对象\)，TRACKER，拖放和菜单合并。  术语激活应用于组件对象模型 \(COM\) \(COM\) 和基于 COM 的对象 \(如 ActiveX 控件。  OLE 自动化现在调用自动化。  
  
## 本节内容  
 [OLE 后台](../mfc/ole-background.md)  
 讨论 OLE 并提供有关它如何的概念性信息有效。  
  
 [激活](../mfc/activation-cpp.md)  
 在编辑活动描述角色 OLE 项。  
  
 [容器](../mfc/containers.md)  
 提供指向使用容器在 OLE。  
  
 [数据对象和数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)  
 提供指向讨论的主题使用 `COleDataObject` 和 `COleDataSource` 类。  
  
 [拖放](../mfc/drag-and-drop-ole.md)  
 使用 OLE 讨论使用复制和粘贴。  
  
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)  
 解释使用菜单和资源的使用。MFC OLE 文档应用程序。  
  
 [注册](../mfc/registration.md)  
 讨论服务器安装和初始化。  
  
 [服务器](../mfc/servers.md)  
 描述如何创建 OLE 项 \(或组件\) 给容器应用程序。  
  
 [跟踪器](../mfc/trackers.md)  
 提供有关 `CRectTracker` 类的信息，该编译器提供了一个图形界面使用户与 OLE 项客户端交互。  
  
## 相关章节  
 [连接点](../mfc/connection-points.md)  
 介绍如何实现连接点 \(原来称作 OLE 连接点\) 使用 MFC 类，`CCmdTarget` 和 `CConnectionPoint`。  
  
 [服务器\/容器 COM 组件](../mfc/containers-advanced-features.md)  
 描述所需步骤中合并选项高级功能到现有的容器应用程序中。  
  
 [组件对象模型 \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 描述使用 OLE，未使用 MFC。  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)