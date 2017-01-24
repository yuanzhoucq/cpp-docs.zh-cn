---
title: "LINGER 结构 | Microsoft Docs"
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
  - "LINGER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LINGER 结构"
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINGER 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`LINGER` 结构用于操作 `CAsyncSocket::GetSockOpt`的 **SO\_LINGER** 和 **SO\_DONTLINGER** 选项。  
  
## 语法  
  
```  
  
      struct linger {  
   u_short l_onoff;            // option on/off  
   u_short l_linger;           // linger time  
};  
```  
  
## 备注  
 当等待未送出的数据发送时，设置 **SO\_DONTLINGER** 选项避免阻止成员函数 **关闭** 。  设置此选项等效于设置 **SO\_LINGER** 且 **l\_onoff** 设置为 0。  
  
## 要求  
 **标头：**winsock2.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)   
 [CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)