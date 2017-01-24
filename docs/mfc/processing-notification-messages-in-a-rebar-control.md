---
title: "处理 Rebar 控件中的通知消息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CReBarCtrl 类, 通知消息发送方"
  - "通知, CReBarCtrl"
  - "RBN_ 通知消息"
  - "RBN_ 通知消息, 说明"
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理 Rebar 控件中的通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 rebar 控件的父类中，请创建一个带有与 switch 语句的 `OnChildNotify` 处理函数处理的所有 rebar 控件 \(`CReBarCtrl`\) 的通知消息。  当用户拖动对象经过 rebar 控件时，或改变 rebar 控件条带的布局时或删除 rebar 控件的条带等情况时，将向其父窗体发送通知的布局。  
  
 下一则通知消息可由 rebar 控件对象发送：  
  
-   在 rebar 自动调整大小时, **RBN\_AUTOSIZE** 由 rebar 控件发送 \(创建具有 **RBS\_AUTOSIZE** 样式 \) 。  
  
-   当用户开始拖动条带时，**RBN\_BEGINDRAG** 被 rebar 控件发送。  
  
-   当条带的子窗口重设大小时，**RBN\_CHILDSIZE** 被 rebar 控件发送。  
  
-   在条带删除之后，**RBN\_DELETEDBAND** 被 rebar 控件发送。  
  
-   当条带将要删除时，**RBN\_DELETINGBAND** 由 rebar 控件发送。  
  
-   当用户停止拖动带时，**RBN\_ENDDRAG** 由 rebar 控件发送。  
  
-   则拖动对象经过一条带时， **RBN\_GETOBJECT** 由 rebar 控件发送 \(创建具有 **RBS\_REGISTERDROP** 样式\)。  
  
-   其高度更改时，**RBN\_HEIGHTCHANGE** 被 rebar 控件发送。  
  
-   当用户更改控件条带的布局时，**RBN\_LAYOUTCHANGED** 被 rebar 控件发送。  
  
 有关这些通知的更多信息，请参见 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 中的 [Rebar 控件引用](http://msdn.microsoft.com/library/windows/desktop/bb774375).  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)