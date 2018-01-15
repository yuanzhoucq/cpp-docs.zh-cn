---
title: "典型 HTTP 客户端应用程序中的步骤 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 936914a816f109736d38259908608b42b7bdcb00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-http-client-application"></a>典型 HTTP 客户端应用程序中的步骤
下表显示了可能在典型的 HTTP 客户端应用程序中执行的步骤：  
  
|您的目标|采取的操作|效果|  
|---------------|----------------------|-------------|  
|开始 HTTP 会话。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|  
|与 HTTP 服务器的连接。|使用[CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)。|返回[CHttpConnection](../mfc/reference/chttpconnection-class.md)对象。|  
|打开 HTTP 请求。|使用[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)。|返回[CHttpFile](../mfc/reference/chttpfile-class.md)对象。|  
|发送 HTTP 请求。|使用[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)和[CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest)。|查找文件。 如果未找到文件，则返回 FALSE。|  
|从文件读取。|使用[CHttpFile](../mfc/reference/chttpfile-class.md)。|读取指定使用您提供的缓冲区的字节数。|  
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|  
|结束 HTTP 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|  
  
## <a name="see-also"></a>请参阅  
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
