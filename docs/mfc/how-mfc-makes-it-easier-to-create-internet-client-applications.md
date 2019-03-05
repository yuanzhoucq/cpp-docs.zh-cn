---
title: MFC 如何简化 Internet 客户端应用程序的创建
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: ffeed3a844fb86acf1bf8c5181c59529824c27f9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300734"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>MFC 如何简化 Internet 客户端应用程序的创建

Microsoft 基础类以可为 MFC 程序员提供熟悉上下文的方式封装 Win32 Internet Extension (WinInet) 函数。 MFC 提供了三种 Internet 文件类 ([CInternetFile](../mfc/reference/cinternetfile-class.md)， [CHttpFile](../mfc/reference/chttpfile-class.md)，并[CGopherFile](../mfc/reference/cgopherfile-class.md)) 派生自[CStdioFile](../mfc/reference/cstdiofile-class.md)类. 通过使用这些类，不仅能使对本地文件使用了 `CStdioFile` 的程序员熟悉 Internet 数据的检索和操作，而且使您能够以一致的透明方式处理本地文件和 Internet 文件。

MFC WinInet 类提供与通过 Internet 传输的数据的 `CStdioFile` 相同的功能。 这些类将针对 HTTP、FTP 和 gopher 的 Internet 协议提取到高级应用程序编程接口，并提供一个快速直接的路径来使应用程序成为 Internet 可识别的应用程序。 例如，对于较低级别的用户来说，连接到 FTP 服务器仍需执行几个步骤，但作为 MFC 开发人员，您只需调用 `CInternetSession::GetFTPConnection` 一次即可创建该连接。

此外，MFC WinInet 类提供了以下好处：

- 缓冲的 I/O

- 数据的类型安全句柄

- 许多函数的默认参数

- 常见 Internet 错误的异常处理

- 打开句柄和连接的自动清理

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[WinInet 如何简化 Internet 客户端应用程序的创建](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)
