---
title: "MessageHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MessageHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MessageHandler function"
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MessageHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**MessageHandler** 是 `MESSAGE_HANDLER` 宏的第二个参数所标识的函数的名称在您的消息映射的。  
  
## 语法  
  
```  
  
      LRESULT   
      MessageHandler  
      (  
   UINT uMsg,  
   WPARAM wParam,  
   LPARAM lParam,  
   BOOL& bHandled  
);  
```  
  
#### 参数  
 `uMsg`  
 指定消息。  
  
 `wParam`  
 其他的消息特定信息。  
  
 `lParam`  
 其他的消息特定信息。  
  
 `bHandled`  
 在 `MessageHandler` 调用之前，消息映射设置 `bHandled` 到 **TRUE**。  如果 `MessageHandler` 不完全处理消息，则应设置 `bHandled` 到 **FALSE** 指示消息需要进一步处理。  
  
## 返回值  
 消息处理结果。  0，如果成功。  
  
## 备注  
 有关使用此消息处理程序在消息映射，请参见 [MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md)。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)