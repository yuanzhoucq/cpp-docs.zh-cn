---
title: "MFC ActiveX 控件：从方法返回错误代码 | Microsoft Docs"
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
  - "错误 [C++], ActiveX 控件错误代码"
  - "FireError 方法"
  - "GetNotSupported 方法"
  - "MFC ActiveX 控件, 错误代码"
  - "SCODE, MFC ActiveX 控件"
  - "SetNotSupported 方法, using"
  - "ThrowError 方法"
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控件：从方法返回错误代码
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍如何从 ActiveX 控件方法返回错误代码。  
  
 若要指示错误方法内发生，应使用 [COleControl::ThrowError](../Topic/COleControl::ThrowError.md) 成员函数的 \(状态代码，采用 `SCODE` 作为参数。\)  可以使用预定义的 `SCODE` 还是定义一个拥有。  
  
> [!NOTE]
>  `ThrowError` 被视为是只能作为返回错误的方法从的属性获取或设置函数或自动化方法内。  这是仅有的时间相应的异常处理程序会存在于堆栈。  
  
 帮助程序函数。常见预定义的 `SCODE`。最存在，如 [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)[COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)[COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)、和。  
  
 有关预定义的 `SCODE`s 和指令列表。定义自定义的 `SCODE`，请参见在 ActiveX 控件的节：[在 ActiveX 控件中的错误处理](../mfc/mfc-activex-controls-advanced-topics.md) 高级主题。  
  
 有关在代码的其他区域的异常报告的更多信息，请参见 [COleControl::FireError](../Topic/COleControl::FireError.md) 和节中的 [在 ActiveX 控件中的错误处理](../mfc/mfc-activex-controls-advanced-topics.md) ActiveX 控件：高级主题。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)