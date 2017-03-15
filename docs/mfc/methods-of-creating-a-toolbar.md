---
title: "创建工具栏的方法 | Microsoft Docs"
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
  - "CToolBar 类, 创建工具栏"
  - "CToolBarCtrl 类, 和 CToolBar 类"
  - "CToolBarCtrl 类, 创建工具栏"
  - "MFC 工具栏"
  - "工具栏控件 [MFC]"
  - "工具栏控件 [MFC], 创建"
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建工具栏的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供了两类创建工具栏：\(打包 Windows 公共控件 API\) 的 [CToolBar](../mfc/reference/ctoolbar-class.md) 和 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)。  `CToolBar` 提供所有工具栏公共控件的功能，因此，在处理很多必需的公共控件设置和您的；结构但是，所得到的可执行的常规大于使用创建 `CToolBarCtrl`。  
  
 `CToolBarCtrl` 通常会带来较小的可执行文件中，因此，您可能更愿意使用 `CToolBarCtrl`，则不应与 MFC 工具栏体系结构。  如果计划使用 `CToolBarCtrl` 和工具栏集成 MFC 结构，必须小心注意其他通信工具栏控件处理到 MFC。  此通信不非常困难；但是，它是不必要的额外工作，使用 `CToolBar`。  
  
 Visual C\+\+ 提供两种工具栏利用公共控件。  
  
-   使用 `CToolBar`，则用于创建工具栏，然后调用 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md) 获取对 `CToolBarCtrl` 成员函数的访问权限。  
  
-   使用 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 构造函数，创建工具栏。  
  
 任一方法允许将工具栏控件的成员函数的访问。  当您调用 `CToolBar::GetToolBarCtrl`时，它返回对 `CToolBarCtrl` 对象的引用，以便可以使用为设置成员函数。  使用 `CToolBar`，请参见 [CToolBar](../mfc/reference/ctoolbar-class.md) 有关构造和创建工具栏的信息。  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)