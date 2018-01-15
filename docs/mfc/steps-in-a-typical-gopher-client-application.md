---
title: "典型 Gopher 客户端应用程序中的步骤 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5108e997336e53434ad33030c0e79be027aa4a98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-gopher-client-application"></a>典型 Gopher 客户端应用程序中的步骤
下表显示了你可能在典型 gopher 客户端应用程序中执行的步骤。  
  
|您的目标|采取的操作|效果|  
|---------------|----------------------|-------------|  
|开始 gopher 会话。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|  
|连接到 gopher 服务器。|使用[CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)。|返回[CGopherConnection](../mfc/reference/cgopherconnection-class.md)对象。|  
|在 gopher 中找到的第一个资源。|使用[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)。|查找第一个文件。 如果未找到文件，则返回 FALSE。|  
|Gopher 中找到的下一步的资源。|使用[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)。|查找下一个文件。 如果未找到文件，则返回 FALSE。|  
|打开文件通过找到**FindFile**或`FindNextFile`以进行读取。|获取使用 gopher 定位器[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|将打开定位符指定的文件。 `OpenFile`返回[CGopherFile](../mfc/reference/cgopherfile-class.md)对象。|  
|打开文件使用你提供 gopher 定位符。|创建使用 gopher 定位符[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|将打开定位符指定的文件。 `OpenFile`返回[CGopherFile](../mfc/reference/cgopherfile-class.md)对象。|  
|从文件读取。|使用[CGopherFile](../mfc/reference/cgopherfile-class.md)。|读取指定的字节，使用您提供的缓冲区数。|  
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|  
|结束 gopher 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|  
  
## <a name="see-also"></a>请参阅  
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
