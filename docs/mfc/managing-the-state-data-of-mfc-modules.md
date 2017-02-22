---
title: "管理 MFC 模块的状态数据 | Microsoft Docs"
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
  - "数据管理 [C++]"
  - "数据管理 [C++], MFC 模块"
  - "导出的接口和全局状态 [C++]"
  - "全局状态 [C++]"
  - "MFC [C++], 管理状态数据"
  - "模块状态已还原"
  - "模块状态, 保存和还原"
  - "多个模块"
  - "窗口过程入口点 [C++]"
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 管理 MFC 模块的状态数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论 MFC 模块状态数据中，并且此状态如何更新，在执行流 \(路径通过代码应用程序，当执行\) 时进入和离开模块。  交换使用 `AFX_MANAGE_STATE` 和 `METHOD_PROLOGUE` 宏的模块状态也进行了讨论。  
  
> [!NOTE]
>  术语“模块”此处是指一个可执行程序，或对 DLL \(或 DLL\) 组独立应用程序的其余运行，但使用 MFC DLL 共享的副本。  ActiveX 控件是模块的典型示例。  
  
 如下图所示，有 MFC 状态数据。在应用程序中的每个模块。  此数据包括窗口的示例 \(实例句柄用于加载资源\)，指向当前 `CWinApp` 和应用程序的 `CWinThread` 对象不同，OLE 模块引用计数，并且，将保留窗口之间的联系的各种对象和句柄映射 MFC 对象的相应实例。  但是，在中，如果应用程序使用的是多模块时，每模块状态数据宽度不是您的应用程序。  相比之下，每模块具有其 MFC 状态数据的私有副本。  
  
 ![单个模块（应用程序）的状态数据](../Image/vc387N1.gif "vc387N1")  
单模块的状态数据（应用程序）  
  
 模块的状态数据以结构包含通过指针并总是可用该结构。  如下图所示，在执行流输入特定模块，模块的状态，必须为“当前”或“活动的”状态。  因此，每一线程对象具有指向该应用程序的有效状态结构。  保持此指针始终更新为管理应用程序的全局状态和维护每模块状态完整性是重要的。  全局状态管理的错误可能导致不可预知应用程序的行为。  
  
 ![多个模块的状态数据](../mfc/media/vc387n2.png "vc387N2")  
多模块状态数据  
  
 也就是说，每模块针对正确的开关运行在模块状态之间的入口点。  “入口点”是执行流可以键入模块的代码的位置。  包含入口点：  
  
-   [在 DLL 的导出函数](../mfc/exported-dll-function-entry-points.md)  
  
-   [COM 接口的成员函数](../mfc/com-interface-entry-points.md)  
  
-   [窗口过程](../mfc/window-procedure-entry-points.md)  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)