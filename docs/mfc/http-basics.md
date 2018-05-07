---
title: HTTP 基础知识 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56a2692edd9d41f80023e44f4ca8172cba8f9d00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="http-basics"></a>HTTP 基础
编写 Internet 应用程序时，您经常在 HTTP 标头中检查并添加信息。 返回代码指示请求的事件是成功还是失败。 下表中列出了一些常用返回代码。  
  
|返回代码|含义|  
|-----------------|-------------|  
|200|找到了 URL，接下来进行传输|  
|400|无法理解的请求|  
|404|找不到请求的 URL|  
|405|服务器不支持请求的方法|  
|500|未知的服务器错误|  
|503|服务不可用|  
  
 HTTP 响应按下表中所示的方式的分组。  
  
|Group|含义|  
|-----------|-------------|  
|200-299|成功|  
|300-399|信息|  
|400-499|请求错误|  
|500-599|服务器错误|  
  
 超文本传输协议 (HTTP) 是超媒体信息系统的应用程序级别协议。 有关 HTTP 以及 Web 浏览器和服务器之间的通信方式的详细信息，请参阅超文本传输协议 (HTTP) 规范：  
  
 [http://www.w3.org/pub/WWW/Protocols/](http://www.w3.org/pub/www/protocols/)  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

