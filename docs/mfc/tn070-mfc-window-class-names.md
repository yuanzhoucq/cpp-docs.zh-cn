---
title: "TN070：MFC 窗口类名称 | Microsoft Docs"
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
  - "vc.mfc.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN070"
  - "窗口类名称"
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN070：MFC 窗口类名称
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 MFC Windows 使用反射功能的 Windows 动态创建的类名。  MFC 提供框架窗口、视图及应用程序生产的弹出窗口动态生成类名。  MFC 应用程序和控件生成的 Windows 对话框具有所提供的名称相关窗口的类。  
  
 通过注册自己的窗口类并将它替换动态提供的类名。[PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)重写。  这些提供 MFC 提供的类名将成为了两下面的某一种形式：  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 `%x` 替换字符的十六进制数字从 [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) 结构的数据填充。  MFC 使用此技术，以便需要相同的 **WNDCLASS** 结构的多个 C\+\+ 类可以共享同一注册的窗口类。  与大多数简单的 Win32 应用程序，" MFC 应用程序只有一个 **WNDPROC**，因此，可以容易地共享 **WNDCLASS** 结构保存时间和内存。  显示的 `%x` 字符的可替换的值前面如下：  
  
-   **WNDCLASS.hInstance**  
  
-   **WNDCLASS.style**  
  
-   **WNDCLASS.hCursor**  
  
-   **WNDCLASS.hbrBackground**  
  
-   **WNDCLASS.hIcon**  
  
 使用第一 \(`Afx:%x:%x`\)，而 **hCursor**、**hbrBackground**和 **hIcon** 是所有 **NULL**时。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)   
 [TN020：ID 命名和编号约定](../mfc/tn020-id-naming-and-numbering-conventions.md)