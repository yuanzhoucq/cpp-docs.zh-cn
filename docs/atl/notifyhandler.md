---
title: "NotifyHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NotifyHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NotifyHandler function"
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# NotifyHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`NOTIFY_HANDLER` 宏的第三个参数标识的函数的名称在您的消息映射的。  
  
## 语法  
  
```  
  
      LRESULT   
      NotifyHandler  
      (  
   int idCtrl,  
   LPNMHDR pnmh,  
   BOOL& bHandled   
);  
```  
  
#### 参数  
 `idCtrl`  
 发送消息的控件的标识符。  
  
 *pnmh*  
 包含通知代码和附加信息 [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) 结构的地址。  对于某些通知消息，此参数指向具有 **NMHDR** 结构作为其第一个成员的更大的结构。  
  
 `bHandled`  
 在 *NotifyHandler* 调用之前，消息映射设置 `bHandled` 到 **TRUE**。  如果 *NotifyHandler* 不完全处理消息，则应设置 `bHandled` 到 **FALSE** 指示消息需要进一步处理。  
  
## 返回值  
 消息处理结果。  0，如果成功。  
  
## 备注  
 有关使用此消息处理程序在消息映射，请参见 [NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md)。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)