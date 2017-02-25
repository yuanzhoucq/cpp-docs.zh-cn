---
title: "注册窗口类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WndProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterWndClass 方法"
  - "类 [C++], 注册窗口类"
  - "MFC, 窗口"
  - "注册窗口类"
  - "注册表, 注册类"
  - "窗口类, 注册"
  - "WinMain 方法"
  - "WinMain 方法, 和注册窗口类"
  - "WndProc 方法"
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 注册窗口类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows传统编程的窗口“类”定义了来自创建的窗口数的类 \(不是 C\+\+ 类\)的特征。  这个类是一个创建窗口的模板或模型。  
  
## 传统程序的窗口类注册窗口  
 在 Windows 的传统程序中，无需 MFC，处理“窗口过程”或“**WndProc**”窗口的所有消息。**WndProc** 与通过“Windows 类注册”进程与窗口关联。  在 `WinMain` 函数中注册主窗口，窗口的其他类可以在应用程序中的任何位置注册。  注册依赖包含**WndProc** 函数的指针与光标，背景画笔等的规范。  结构作为参数与类的字符串名称一起传递，优先调用 **RegisterClass** 函数。  因此，注册类可以由多个窗口共享。  
  
## MFC程序的窗口类注册  
 相比之下，大多数窗口类注册在MFC 框架计划中自动完成。  如若使用 MFC，从继承关系中使用常规 C\+\+ 语法从现有库类继承窗体类。  框架还使用传统“注册类”，它为您提供几标准组成部分，在需要时注册。  您可以通过调用 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全局函数，然后将注册类传递给`CWnd`的 **Create** 成员函数。  如此处描述，传统“注册”类窗口不会与 C\+\+ 类相混淆。  
  
 有关更多信息，请参见 [Technical Note 1](../mfc/tn001-window-class-registration.md)。  
  
## 请参阅  
 [创建窗口](../mfc/creating-windows.md)