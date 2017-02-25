---
title: "如何：使用消息映射交叉引用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "窗口 [C++], 消息映射"
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：使用消息映射交叉引用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在入口标记 \<memberFxn 处\>，请为派生类[CWnd](../../mfc/reference/cwnd-class.md)编写自己的成员函数。  函数为您喜欢的任何名称。  其他函数，如 `OnActivate`，是 `CWnd`类的成员函数。  如果被调用，则将消息传递给  `DefWindowProc`Windows 函数。  要处理通知窗口消息，需要重写派生类`CWnd`中相应的函数。  你的函数应调用基类中的重写函数使基类和 Windows响应消息。  
  
 在任何情况下，请将函数原型放在 `CWnd`派生类标头中，并且编写消息映射。  
  
 使用了以下术语：  
  
|术语|定义|  
|--------|--------|  
|id|任何用户定义菜单项的 ID \(**WM\_COMMAND** 消息 ID\) 或控件 \(子窗口的通知消息\)。|  
|“信息”和“wNotifyCode”|在 WINDOWS.H 中定义的Windows消息ID。|  
|nMessageVariable|一个包含了 **RegisterWindowMessage** Windows 函数的返回值的变量的名称。|  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)