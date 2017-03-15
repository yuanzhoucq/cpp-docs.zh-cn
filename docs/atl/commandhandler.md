---
title: "CommandHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CommandHandler function"
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CommandHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CommandHandler` 是 `COMMAND_HANDLER` 宏的第三个参数确定的函数在您的消息映射的。  
  
## 语法  
  
```  
  
      LRESULT   
      CommandHandler  
      (  
   WORD wNotifyCode,  
   WORD wID,  
   HWND hWndCtl,  
   BOOL& bHandled   
);  
```  
  
#### 参数  
 `wNotifyCode`  
 通知代码。  
  
 *wID*  
 菜单项、控件或快捷键的标识符。  
  
 *hWndCtl*  
 为windows控件的句柄。  
  
 `bHandled`  
 在 `CommandHandler` 调用之前，消息映射设置 `bHandled` 到 **TRUE**。  如果 `CommandHandler` 不完全处理消息，则应设置 `bHandled` 到 **FALSE** 指示消息需要进一步处理。  
  
## 返回值  
 消息处理结果。  0，如果成功。  
  
## 备注  
 有关使用此消息处理程序在消息映射，请参见 [COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md)。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)   
 [Message Maps](../atl/message-maps-atl.md)   
 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)