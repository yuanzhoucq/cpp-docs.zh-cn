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
ms.openlocfilehash: 9201859c6a5d9fe2b31c3fc4348a42ff9566fc8c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326278"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>用于创建 Internet 客户端应用程序的 MFC 类

MFC 提供了编写 Internet 客户端应用程序的以下类和全局函数。 缩进指示从其上未缩进行的类派生的类。 `CGopherFile` 并`CHttpFile`派生自`CInternetFile`，例如。 这些类和全局函数 AFXINET 中声明。H，除`CFileFind`，AFX 中声明。H.

## <a name="classes"></a>类

- [CInternetSession](../mfc/reference/cinternetsession-class.md)

- [CInternetConnection](../mfc/reference/cinternetconnection-class.md)

   - [CFtpConnection](../mfc/reference/cftpconnection-class.md)

   - [CGopherConnection](../mfc/reference/cgopherconnection-class.md)

   - [CHttpConnection](../mfc/reference/chttpconnection-class.md)

- [CInternetFile](../mfc/reference/cinternetfile-class.md)

   - [CGopherFile](../mfc/reference/cgopherfile-class.md)

   - [CHttpFile](../mfc/reference/chttpfile-class.md)

- [CFileFind](../mfc/reference/cfilefind-class.md)

   - [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)

   - [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)

- [CGopherLocator](../mfc/reference/cgopherlocator-class.md)

- [CInternetException](../mfc/reference/cinternetexception-class.md)

## <a name="global-functions"></a>全局函数

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
