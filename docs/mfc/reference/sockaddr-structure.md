---
title: "SOCKADDR 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR 结构"
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# SOCKADDR 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`SOCKADDR` 结构用于机器参与 Windows 套接字通信时存储网络协议（IP）地址。  
  
## 语法  
  
```  
  
      struct sockaddr {  
   unsigned short sa_family;  
   char sa_data[14];  
};  
```  
  
#### 参数  
 *sa\_family*  
 套接字地址族。  
  
 *sa\_data*  
 所有不同的套接字地址结构的最大尺寸。  
  
## 备注  
 微软 TCP\/IP 套接字开发者工具包仅支持 Internet 地址域。  实际上，为了填写地址的每个部分值，请使用 `SOCKADDR_IN` 数据结构，它是专门用于该地址形式的。  `SOCKADDR` 和 `SOCKADDR_IN` 数据结构具有相同的大小。  你只需在两种结构类型之间进行转换。  
  
## 要求  
 **标头：**winsock2.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR\_IN 结构](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)