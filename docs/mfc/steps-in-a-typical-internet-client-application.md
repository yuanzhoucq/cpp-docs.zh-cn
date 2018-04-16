---
title: "典型 Internet 客户端应用程序中的步骤 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce4f5b91ebd68f13510f887c65927dbe5f84133
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-internet-client-application"></a>典型 Internet 客户端应用程序中的步骤
下表显示了你可能会执行典型 Internet 客户端应用程序中的步骤。  
  
|您的目标|采取的操作|效果|  
|---------------|----------------------|-------------|  
|开始 Internet 会话。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|  
|设置一个 Internet 查询选项 （超时限制或的重试次数，例如）。|使用[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)。|如果操作不成功，则返回 FALSE。|  
|建立监视会话的状态的回调函数。|使用[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)。|建立到回调[CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)。 重写`OnStatusCallback`创建你自己的回调例程。|  
|连接到 Internet 服务器、 intranet 服务器或本地文件。|使用[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。|分析 URL 并打开与指定的服务器的连接。 返回[CStdioFile](../mfc/reference/cstdiofile-class.md) (如果你通过`OpenURL`本地文件名)。 这是通过其访问的服务器或文件从检索数据的对象。|  
|从文件读取。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|读取指定使用您提供的缓冲区的字节数。|  
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|  
|结束 Internet 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|  
  
## <a name="see-also"></a>请参阅  
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
