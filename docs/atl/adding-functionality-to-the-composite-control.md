---
title: "Adding Functionality to the Composite Control | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 事件"
  - "复合控件, 处理事件"
  - "event handlers [C++], ActiveX 控件"
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Functionality to the Composite Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一旦插入到所需的所有控件到复合控件，下一步中添加新功能。  此新功能通常分为两类:  
  
-   支持附加接口和自定义您的复合控件行为与另外，特定功能。  
  
-   处理从包含的ActiveX控件\(或控件\)的事件。  
  
 对目标和大小本文，本节的其余部分都关注处理从ActiveX控件的事件。  
  
> [!NOTE]
>  如果需要从Windows控件中处理消息，请参见 [实现窗口](../atl/implementing-a-window.md) 有关消息处理在ATL的更多信息。  
  
 在插入ActiveX控件后在对话框资源，请右击该控件并单击 **添加事件处理程序**。  选择要处理的事件并单击 **Add and Edit**。  事件处理程序代码将添加到控件的.h文件。  
  
 有关该复合控件的ActiveX控件连接点会自动连接，并能够通过调用 [CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)。  
  
## 请参阅  
 [复合控件基础知识](../atl/atl-composite-control-fundamentals.md)