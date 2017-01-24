---
title: "处理反射消息 | Microsoft Docs"
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
  - "消息处理, 反映的消息"
  - "反映的消息, 处理"
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理反射消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反射消息可以处理消息的控件，如控件自身的 `WM_CTLCOLOR`、**WM\_COMMAND**和 **WM\_NOTIFY**。  这样控件更独立和可迁移。  机制使用 Windows 公共控件以及与 ActiveX 控件工作 \(原名为 OLE 控件\)。  
  
 反射消息可以方便地重用 `CWnd`派生类。  使用特殊的 **ON\_XXX\_REFLECT** 消息映射项，反射消息通过 [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)工作，例如：例如，**ON\_CTLCOLOR\_REFLECT** 和 **ON\_CONTROL\_REFLECT**。  [技术说明 62](../mfc/tn062-message-reflection-for-windows-controls.md) 更详细地介绍消息反射。  
  
## 你希望做什么？  
  
-   [了解有关反射消息](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [实现一种公共控件的反射消息](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [实现 ActiveX 控件的反射消息](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## 请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)