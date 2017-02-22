---
title: "SOCKADDR_IN 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR_IN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR_IN 结构"
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# SOCKADDR_IN 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Internet 地址族中，Windows 套接字使用 `SOCKADDR_IN` 来指定连接套接字的本地或远程端点地址。  
  
## 语法  
  
```  
  
      struct sockaddr_in{  
   short sin_family;  
   unsigned short sin_port;  
   struct in_addr sin_addr;  
   char sin_zero[8];  
};  
```  
  
#### 参数  
 *sin\_family*  
 地址系列（必须是 **AF\_INET**）。  
  
 *sin\_port*  
 IP 端口。  
  
 *sin\_addr*  
 IP 地址。  
  
 *sin\_zero*  
 填充结构使其与 `SOCKADDR` 的大小一致。  
  
## 备注  
 这是特定于 Internet 地址族并可转换为 `SOCKADDR` 的 `SOCKADDR` 结构窗体。  
  
 此结构的 IP 地址组件是 **IN\_ADDR** 类型。  **IN\_ADDR** 结构在 Windows 套接字标头文件 WINSOCK.H 中定义如下：  
  
 `struct   in_addr {`  
  
 `union   {`  
  
 `struct{`  
  
 `unsigned  char   s_b1,`  
  
 `s_b2,`  
  
 `s_b3,`  
  
 `s_b4;`  
  
 `}  S_un_b;`  
  
 `struct  {`  
  
 `unsigned  short  s_w1,`  
  
 `s_w2;`  
  
 `}  S_un_w;`  
  
 `unsigned long  S_addr;`  
  
 `} S_un;`  
  
 `};`  
  
## 要求  
 **标头：**winsock2.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR 结构](../../mfc/reference/sockaddr-structure.md)