---
title: "创建状态栏的方法 | Microsoft Docs"
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
  - "CStatusBar 类, 与 CStatusBarCtrl"
  - "CStatusBarCtrl 类, 创建"
  - "CStatusBarCtrl 类, 与 CStatusBar"
  - "方法 [MFC]"
  - "方法 [MFC], 创建状态栏"
  - "状态栏, 创建"
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建状态栏的方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供了两类创建状态栏：\(打包 Windows 公共控件 API\) 的 [CStatusBar](../mfc/reference/cstatusbar-class.md) 和 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)。  `CStatusBar` 提供所有状态栏公共控件的功能，其与菜单和工具栏自动交互，因此，在处理很多必需的公共控件设置和您的；结构但是，所得到的可执行的常规大于使用创建 `CStatusBarCtrl`。  
  
 `CStatusBarCtrl` 通常会带来较小的可执行文件中，因此，您可能更愿意使用 `CStatusBarCtrl`，则不应将状态栏 MFC 体系结构。  如果计划使用 `CStatusBarCtrl` 和集成 MFC 状态栏结构，必须小心注意其他的传达状态栏控件处理到 MFC。  此通信不非常困难；但是，它是不必要的额外工作，使用 `CStatusBar`。  
  
 Visual C\+\+ 提供两种状态栏使用公共控件。  
  
-   使用 `CStatusBar`创建状态栏，然后调用 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md) 获取对 `CStatusBarCtrl` 成员函数的访问权限。  
  
-   使用 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) 构造函数，创建状态栏。  
  
 任一方法允许您为状态栏控件的成员函数的访问。  当您调用 `CStatusBar::GetStatusBarCtrl`时，它返回对 `CStatusBarCtrl` 对象的引用，以便可以使用为设置成员函数。  使用 `CStatusBar`，请参见 [CStatusBar](../mfc/reference/cstatusbar-class.md) 有关构造和创建状态栏的信息。  
  
## 请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)