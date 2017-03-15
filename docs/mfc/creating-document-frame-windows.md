---
title: "创建文档框架窗口 | Microsoft Docs"
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
  - "文档框架窗口, 创建"
  - "文档模板, 和文档框架窗口"
  - "框架窗口 [C++], 创建"
  - "MFC [C++], 框架窗口"
  - "运行时类, 和文档框架窗口创建"
  - "运行时, 类信息"
  - "窗口 [C++], 创建"
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 创建文档框架窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查看[文档\/视图创建](../mfc/document-view-creation.md) [CDocTemplate](../mfc/reference/cdoctemplate-class.md) 对象如何安排创建框架窗口、文档及视图和一起连接它们全部。  给 `CDocTemplate` 构造函数的参数指定三 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 框架窗口，文档，并且显示文档模板动态创建根据用户命令 \(如在"文件"菜单上的新命令或 MDI 窗口"菜单上的"新建窗口"命令的类。  在创建视图和文档的，则一框架窗口、文档模板将此信息存储以供将来使用。  
  
 为了使变换正确工作 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) 的机制，必须声明派生的框架窗口类与 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 宏。  这是因为，需要文档框架创建框架窗口使用类 `CObject`的构造动态机制。  
  
 在用户选择创建文档的命令时，框架要求文档模板创建文档对象、其视图和查看视图的框架窗口。  在创建文档框架窗口时，文档模板创建适当的类 \(从 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 从派生的应用程序 [CFrameWnd](../mfc/reference/cframewnd-class.md) 的 SDI 或类的对象负责 MDI 应用程序。  框架将调用框架窗口对象的成员函数 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 从资源获取创建消息创建窗口和窗口。  框架附加窗口句柄到框架窗口对象。  然后它创建视图，文档框架窗口的子窗口。  
  
 请在 [时初始化](../mfc/when-to-initialize-cwnd-objects.md) 决定 `CWnd`派生的对象。  
  
## 您想进一步了解什么？  
  
-   [从派生类 CObject \(其动态创建机制\)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [文档\/视图创建 \(模板和框架窗口创建\)](../mfc/document-view-creation.md)  
  
-   [销毁框架窗口](../mfc/destroying-frame-windows.md)  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)