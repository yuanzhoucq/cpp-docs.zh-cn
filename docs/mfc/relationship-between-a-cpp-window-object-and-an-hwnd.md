---
title: "C++ 窗口对象与 HWND 之间的关系 | Microsoft Docs"
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
  - "HWND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 类, HWND"
  - "HWND"
  - "HWND, 窗口对象"
  - "窗口对象 [C++], HWND 和"
  - "Windows 窗口 [C++]"
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 窗口对象与 HWND 之间的关系
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

窗口 *对象* 是程序直接创建 C\+\+ `CWnd` 类 \(或派生类\) 的对象。  但它造成往往是响应程序的构造函数和析构函数。  窗口 *窗口*，另一方面，是不透明句柄到对应于 Windows 的内部 Windows 数据结构并使用系统资源，当存在。  窗口窗口由“Windows 句柄”确定 \(`HWND`\)，以及创建在 `CWnd` 对象创建为类通过调用 `CWnd`的 **创建** 成员函数。  窗口可能会销毁或一个由程序调用或通过用户操作。  窗口句柄。窗口对象的 `m_hWnd` 成员变量存储。  下图演示对象 C\+\+ Windows 和 Windows 窗口之间的关系。  创建窗口中 [创建窗口](../mfc/creating-windows.md)讨论。  销毁窗口中 [窗口销毁的对象](../mfc/destroying-window-objects.md)讨论。  
  
 ![CWnd 窗口对象和生成的窗口](../mfc/media/vc37fj1.png "vc37FJ1")  
窗口对象和 Windows 窗口  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)