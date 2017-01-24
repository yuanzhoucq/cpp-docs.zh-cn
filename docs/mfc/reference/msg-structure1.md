---
title: "MSG 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MSG 结构"
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MSG 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MSG` 结构包含从线程的消息队列的信息段。  
  
## 语法  
  
```  
  
      typedef struct tagMSG {     // msg    
   HWND hwnd;  
   UINT message;  
   WPARAM wParam;  
   LPARAM lParam;  
   DWORD time;  
   POINT pt;  
} MSG;  
```  
  
#### 参数  
 *hwnd*  
 标识窗口过程接收消息的窗口。  
  
 `message`  
 指定消息号。  
  
 `wParam`  
 指定有关消息的更多信息。  确切含义取决于 **message** 成员的值。  
  
 `lParam`  
 指定有关消息的更多信息。  确切含义取决于 **message** 成员的值。  
  
 `time`  
 指定传递消息时的时间。  
  
 `pt`  
 当传递消息时指定了，光标位置，在屏幕坐标。  
  
## 要求  
 **页眉：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)