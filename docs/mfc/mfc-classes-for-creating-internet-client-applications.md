---
title: 用于创建 Internet 客户端应用程序的 MFC 类
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: 578fd5b72e6c04610aa862f1a6631895a32a9bfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358219"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>用于创建 Internet 客户端应用程序的 MFC 类

MFC 提供以下类和全局函数来编写 Internet 客户端应用程序。 缩进表示类派生自其上方的未缩进类。 `CGopherFile`并`CHttpFile`派生自`CInternetFile`，例如。 这些类和全局函数在 AFXINET 中声明。H，AFX 中声明的 除外`CFileFind`。H。

## <a name="classes"></a>类

- [C 互联网会话](../mfc/reference/cinternetsession-class.md)

- [C 互联网连接](../mfc/reference/cinternetconnection-class.md)

  - [CFtpConnection](../mfc/reference/cftpconnection-class.md)

  - [CGopherConnection](../mfc/reference/cgopherconnection-class.md)

  - [CHttpConnection](../mfc/reference/chttpconnection-class.md)

- [C互联网文件](../mfc/reference/cinternetfile-class.md)

  - [CGopherFile](../mfc/reference/cgopherfile-class.md)

  - [CHttpFile](../mfc/reference/chttpfile-class.md)

- [CFileFind](../mfc/reference/cfilefind-class.md)

  - [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)

  - [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [C 互联网例外](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>全局功能

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>另请参阅

[Win32 互联网扩展（WinInet）](../mfc/win32-internet-extensions-wininet.md)<br/>
[互联网客户端类的先决条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写互联网客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
