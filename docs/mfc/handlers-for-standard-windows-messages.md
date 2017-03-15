---
title: "标准 Windows 消息的处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afx_msg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数 [C++], 处理程序"
  - "处理函数, 标准 Windows 消息"
  - "消息处理 [C++], Windows 消息处理程序"
  - "消息 [C++], Windows"
  - "Windows 消息 [C++], 处理程序"
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 标准 Windows 消息的处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标准 Windows 消息 \(**WM\_**\) 的默认处理程序在类 `CWnd`中预定义。  这些处理程序的类库名称基于消息名称。  例如，`WM_PAINT` 消息的处理程序在`CWnd` 中声明，如下：  
  
 `afx_msg void OnPaint();`  
  
 **afx\_msg** 关键字显示 C\+\+ **virtual** 关键字的效果，通过来自其他`CWnd` 成员函数的识别处理程序。  然而，请注意，这些函数不是虚拟的；实际上它们通过消息映射实现。  消息映射仅取决于条件预处理器宏，而不是任何对 C\+\+ 语言的扩展。  预处理后**afx\_msg** 关键字解析为空格。  
  
 若要在基类中重写处理程序定义，在由的派生类中简单定义具有同一原型的函数，为处理程序提供一个消息映射输入。  在任一类的基类中，处理程序“重写”同一名称的任何处理程序。  
  
 在某些情况下，您的处理程序应当在基类中调用重写的处理程序，因此基类\(es\)和窗口可在消息中进行操作。  何处调用重写的基类处理程序取决于条件。  有时必须首先调用基类，有时最后调用。  有时，如果选择不处理消息，可以有条件地调用基类处理程序。  有时应调用基类处理程序，然后是有条件地执行自己的处理程序代码，这取决于基类处理程序或状态返回的值。  
  
> [!CAUTION]
>  修改参数传入处理程序是不安全的，如果要传递它们到基类处理程序。  例如，您可能会临时修改 `OnChar` 处理程序的 `nChar` 参数 \(如转换为大写\)。  此行为非常见，但是如果您需要完成此效果，使用 `CWnd` 成员函数 **SendMessage**替代。  
  
 如何确定合适的方法重写一给定的消息？  在属性窗口编写给定消息的处理程序函数的主干时 — `WM_CREATE`的 `OnCreate` 处理程序，例如—描述建议重写成员函数的窗体。  下面的示例建议处理程序首先调用基类处理程序并运行，只有在不返回 \- 1的情况下。  
  
 [!CODE [NVC_MFCMessageHandling#3](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#3)]  
  
 按照约定，这些处理程序的名称以"On."前缀开头。处理程序不采用参数而其他使用数个参数。  一些具有返回类型而不是 `void`。  在*MFC 参考*中，所有 **WM\_** 消息的默认处理程序作为类`CWnd` 的成员函数，该类名以 "On."开头。`CWnd` 中的成员函数声明以 **afx\_msg**为前缀。  
  
## 请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)