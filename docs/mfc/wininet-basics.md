---
title: WinInet 基础知识
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: 79ec102aa27440c64f03c6e22b9f2fe959cac6b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399546"
---
# <a name="wininet-basics"></a>WinInet 基础知识

可以使用 WinInet 添加 FTP 支持，以下载和上传从你的应用程序中的文件。 您可以重写[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)并用*dwContext*参数向用户提供进度信息，如搜索并下载文件。

本文包含以下主题：

- [创建非常简单的浏览器](#_core_create_a_very_simple_browser)

- [下载 Web 页](#_core_download_a_web_page)

- [FTP 文件](#_core_ftp_a_file)

- [检索 Gopher 目录](#_core_retrieve_a_gopher_directory)

- [显示进度信息，同时将文件传输](#_core_display_progress_information_while_transferring_files)

下面的代码摘录内容演示如何创建简单的浏览器，下载网页，ftp 传输文件，并搜索 gopher 文件。 它们并不完整的示例并不是所有包含异常处理。

WinInet 的其他信息，请参阅[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)。

##  <a name="_core_create_a_very_simple_browser"></a> 创建非常简单的浏览器

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> 下载 Web 页

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> FTP 文件

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> 检索 Gopher 目录

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>使用 OnStatusCallback

使用 WinInet 类时，可以使用[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)的应用程序的成员[CInternetSession](../mfc/reference/cinternetsession-class.md)对象来检索状态信息。 如果派生您自己`CInternetSession`对象，请重写`OnStatusCallback`，并启用状态回调，MFC 将调用你`OnStatusCallback`函数和该 Internet 会话中所有活动的进度信息。

因为单个会话可能支持多个连接 （其中，对它们的生存期内可能会执行许多不同的非重复操作），`OnStatusCallback`需要一种机制来标识具有特定的连接或事务的每个状态更改。 该机制提供的上下文 ID 参数提供给许多 WinInet 支持类中的成员函数。 此参数的类型始终是**DWORD** ，并始终命名为*dwContext*。

分配给特定的 Internet 对象的上下文仅用于标识该对象会导致的活动`OnStatusCallback`的成员`CInternetSession`对象。 对调用`OnStatusCallback`接收多个参数; 这些参数协同工作以告知应用程序的事务和连接已对哪些进度。

当您创建`CInternetSession`对象，可以指定*dwContext*构造函数参数。 `CInternetSession` 本身不会使用的上下文 ID;相反，它将传递到任何的上下文 ID **InternetConnection**-派生的对象的显式不获取其自己的上下文 ID。 接下来，那些`CInternetConnection`对象将传递到此过程的上下文 ID`CInternetFile`对象它们创建如果未显式指定一个不同的上下文 id。 如果手动，指定你自己的一个特定的上下文 ID、 对象和它执行任何工作将与相关联的上下文 id。 可以使用上下文 Id 来标识哪些状态信息正在向你提供了你`OnStatusCallback`函数。

##  <a name="_core_display_progress_information_while_transferring_files"></a> 显示进度信息，同时将文件传输

例如，如果您编写的应用程序创建一个与读取文件的 FTP 服务器连接和同时连接到 HTTP 服务器来获取一个网页，则必须`CInternetSession`对象、 两`CInternetConnection`对象 (一个是`CFtpSession`和另一个将是`CHttpSession`)，并将两个`CInternetFile`对象 （一个用于每个连接）。 如果使用的默认值*dwContext*参数，您将不能区分`OnStatusCallback`指示 FTP 连接和的调用中指示的进度的进度的调用HTTP 连接。 如果指定*dwContext* ID，您可以更高版本以测试`OnStatusCallback`，您将知道哪个操作生成回调。

## <a name="see-also"></a>请参阅

[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
