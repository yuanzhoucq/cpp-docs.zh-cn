---
title: "HTTP 基础 | Microsoft Docs"
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
  - "HTTP 请求, 返回代码"
  - "HTTP, 返回代码"
  - "返回代码"
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HTTP 基础
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编写在 Internet 应用程序时，您经常检查并添加到将在 HTTP 头的信息。  返回代码指示请求事件的成功或失败。  若干常用返回代码在下表中列出。  
  
|返回代码|含义|  
|----------|--------|  
|200|定位的 URL，在传输|  
|400|难以理解的请求|  
|404|Requests Not Found（未找到的请求数）|  
|405|服务器不支持请求的方法|  
|500|未知的服务器错误。|  
|503|服务不可用|  
  
 下表显示了如下选项  
  
|Group|含义|  
|-----------|--------|  
|200–299|成功|  
|300–399|信息|  
|400–499|请求错误|  
|500–599|Server error|  
  
 超文本传输协议 \(HTTP\) 是超媒体信息系统的应用程序级别协议。  有关 HTTP 的更多信息，以及 Web 浏览器和服务器之间如何通信，请参见超文本传输协议 \(HTTP\) 规范：  
  
 [http:\/\/www.w3.org\/pub\/WWW\/Protocols\/](http://www.w3.org/pub/WWW/Protocols/)  
  
## 请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)