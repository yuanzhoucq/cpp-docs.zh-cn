---
title: "活动文档服务器 | Microsoft Docs"
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
  - "活动文档服务器 [C++]"
  - "活动文档 [C++], 服务器"
  - "服务器 [C++], 活动文档"
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 活动文档服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

活动文档服务器 ，如称为本地文档的其他应用程序类型的 Word、Excel或PowerPoint主机文档。  与 OLE 嵌入对象不同（简略显示其他文档的页面），活动文档提供整接口并完成创建这些服务器应用程序的原有功能。  用户使用它们收藏夹应用程序的全功能创建文档 \(如果它们处于活动文档\)，因此，可以将产生的项目作为一个实体。  
  
 活动文档中有多页并始终处于就地活动状态。  用户的界面活动文档控件部件，将其菜单与容器的 **文件** 和 **帮助**菜单合并。  它们占据整个容器的编辑区域、控件视图和打印机页 \(边距，页脚，等等\)。  
  
 MFC 实现带有文档\/视图接口、命令映射计划、打印、菜单和管理注册表管理的活动文档服务器。  在[活动文档](../mfc/active-documents.md)中讨论特定的编程要求。  
  
 MFC 支持与 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) 类的活动文档，派生自 [CCmdTarget](../mfc/reference/ccmdtarget-class.md), [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)派生自[COleServerItem](../mfc/reference/coleserveritem-class.md).  MFC 支持带有 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) 类的活动文档容器，派生自 [COleClientItem](../mfc/reference/coleclientitem-class.md)。  
  
 `CDocObjectServer` 映射活动文档界面 \(MDI\) 和初始化以及激活活动文档。  MFC 还提供对宏以处理在活动文档的路由命令。  在应用程序中使用活动文档，包括 StdAfx.h 文件中的 AfxDocOb.h。  
  
 标准 MFC 服务器联接自己的 `COleServerItem`\-派生类。  如果选择了 **Mini\-server** 或 **Full\-server** 复选框提供应用程序服务器复合文档支持，MFC 应用程序向导为您生成此类。  如果也选中 **活动文档服务器 \(A\)** 复选框，MFC 应用程序向导生成一个从 `CDocObjectServerItem` 派生的类。  
  
 `COleDocObjectItem` 类允许OLE容器成为活动文档容器。  可以使用 MFC 应用程序向导通过在 MFC 应用程序向导的组合文档支持页的 **活动文档容器 \(D\)** 复选框以创建活动文档容器。  有关更多信息，请参见 [创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。  
  
## 请参阅  
 [活动文档包容](../mfc/active-document-containment.md)