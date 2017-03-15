---
title: "Using Contained Windows | Microsoft Docs"
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
  - "contained windows in ATL"
  - "windows [C++], ATL"
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using Contained Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL实现包含了 [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)的窗口。  一个包含窗口表示将其消息发送到容器对象而不是处理它们在其自己的选件类的窗口。  
  
> [!NOTE]
>  不必从 `CContainedWindowT` 派生选件类才能使用包含窗口。  
  
 包含窗口，可以创建超类时现有Windows选件类或子类现有的窗口。  会创建现有Windows选件类，构造函数首先指定现有类名。`CContainedWindowT` 对象的窗口。  然后调用 `CContainedWindowT::Create`。  对子类现有的窗口，无需指定Windows类名\(向构造函数传递 **NULL** ）。  调用与处理的 `CContainedWindowT::SubclassWindow` 方法到子类的窗口。  
  
 在容器的数据成员类别，通常使用包含窗口。  容器不必是windows;但是，它必须从 [CMessageMap](../atl/reference/cmessagemap-class.md)派生。  
  
 一个包含窗口可以使用替换消息映射来处理其消息。  如果您有多个包含窗口，应声明了替换消息映射，其中每个计数器都有单独包含窗口相对应。  
  
## 示例  
 以下容器选件类的示例使用两个包含窗口的:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/CPP/using-contained-windows_1.h)]  
  
 有关包含窗口的更多信息，请参见 [SUBEDIT](../top/visual-cpp-samples.md) 示例。  
  
## 请参阅  
 [窗口类](../atl/atl-window-classes.md)