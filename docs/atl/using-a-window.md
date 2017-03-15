---
title: "Using a Window | Microsoft Docs"
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
  - "ATL, 窗口"
  - "CWindow class, about CWindow class"
  - "windows [C++], ATL"
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using a Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

选件类 [CWindow](../atl/reference/cwindow-class.md) 允许您使用窗口。  一旦附加到windows `CWindow` 对象，然后可以调用 `CWindow` 方法操作窗口。  `CWindow` 还包含一 `HWND` 运算符转换为 `HWND`的一 `CWindow` 对象。  因此可以传递给需要一个窗口的句柄的所有功能的一 `CWindow` 对象。  您可以轻松地组合 `CWindow` 方法调用，并且Win32函数调用，尚未创建任何临时对象。  
  
 由于 `CWindow` 只有两个数据成员\(windows句柄和默认维度\)，则不会开销使您的代码。  此外，许多 `CWindow` 方法对应的Win32 API函数。  使用 `CWindow`，`HWND` 成员将自动传递给Win32函数。  
  
 除了直接使用 `CWindow` 外，还可以从它还派生添加数据或代码添加到您的选件类。  ATL从派生 `CWindow`三选件类: [CWindowImpl](../atl/implementing-a-window.md)、 [CDialogImpl](../atl/implementing-a-dialog-box.md)和 [CContainedWindowT](../atl/using-contained-windows.md)。  
  
## 请参阅  
 [窗口类](../atl/atl-window-classes.md)