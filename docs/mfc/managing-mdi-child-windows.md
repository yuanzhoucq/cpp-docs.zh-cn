---
title: "管理 MDI 子窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MDICLIENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子窗口"
  - "子窗口, 和 MDICLIENT 窗口"
  - "框架窗口 [C++], MDI 子窗口"
  - "MDI [C++], 子窗口"
  - "MDI [C++], 框架窗口"
  - "MDICLIENT 窗口"
  - "窗口 [C++], MDI"
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 管理 MDI 子窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MDI 主框架窗口 \(每个应用程序一个 \) 包含一个称为**MDICLIENT**窗口的特定子窗口。  **MDICLIENT** 窗口管理主框架窗口的工作区，并且其自身具有子窗口：文档窗口派生自 `CMDIChildWnd`。  由于文档窗口是框架窗口 \( MDI 子窗口\)，它们也有自己的子项。  除这些情况，父窗口管理其子窗口和转寄这些命令给它们。  
  
 在 MDI 框架窗口，框架窗口管理 **MDICLIENT** 窗口，在结合处用控件条重新定位它们。  **MDICLIENT** 窗口，反过来，管理所有 MDI 子框架窗口。  下图显示 MDI 框架窗，其 **MDICLIENT** 窗口与子文档框架窗口之间的关系。  
  
 ![MDI 框架窗口中的子窗口](../mfc/media/vc37gb1.png "vc37GB1")  
MDI 框架窗口和子窗口  
  
 如果这儿有，MDI 框架窗口与当前 MDI 子窗口也有效。  在MDI 框架窗口试着处理向它们之前，MDI 框架窗口委托命令消息给 MDI 子窗口。  
  
## 您想进一步了解什么？  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)