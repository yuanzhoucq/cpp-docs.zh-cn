---
title: 典型 HTTP 客户端应用程序中的步骤
ms.date: 11/04/2016
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
ms.openlocfilehash: 59b585d3e6b8c9f13c585f5a712d33abd6123f67
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296470"
---
# <a name="steps-in-a-typical-http-client-application"></a>典型 HTTP 客户端应用程序中的步骤

下表显示了可能会执行典型 HTTP 客户端应用程序中的步骤：

|您的目标|采取的操作|Effects|
|---------------|----------------------|-------------|
|开始 HTTP 会话。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|
|连接到 HTTP 服务器。|使用[cinternetsession:: Gethttpconnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)。|返回[CHttpConnection](../mfc/reference/chttpconnection-class.md)对象。|
|打开 HTTP 请求。|使用[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)。|返回[CHttpFile](../mfc/reference/chttpfile-class.md)对象。|
|发送 HTTP 请求。|使用[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)并[CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest)。|查找文件。 如果未找到文件，则返回 FALSE。|
|从文件中读取。|使用[CHttpFile](../mfc/reference/chttpfile-class.md)。|读取指定使用您提供的缓冲区的字节数。|
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|
|结束 HTTP 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
