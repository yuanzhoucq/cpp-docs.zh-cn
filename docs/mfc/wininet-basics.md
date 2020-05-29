---
title: WinInet 基础知识
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367326"
---
# <a name="wininet-basics"></a>WinInet 基础知识

您可以使用 WinInet 添加 FTP 支持，以便从应用程序内下载和上传文件。 您可以覆盖[OnStatusCallback，](../mfc/reference/cinternetsession-class.md#onstatuscallback)并使用*dwContext*参数在搜索和下载文件时向用户提供进度信息。

本文包含以下主题：

- [创建非常简单的浏览器](#_core_create_a_very_simple_browser)

- [下载网页](#_core_download_a_web_page)

- [FTP 文件](#_core_ftp_a_file)

- [检索 Gopher 目录](#_core_retrieve_a_gopher_directory)

- [传输文件时显示进度信息](#_core_display_progress_information_while_transferring_files)

下面的代码摘录演示如何创建简单的浏览器、下载网页、FTP 文件以及搜索 gopher 文件。 它们不是作为完整示例，也不都包含异常处理。

有关 WinInet 的更多信息，请参阅[Win32 互联网扩展 （WinInet）。](../mfc/win32-internet-extensions-wininet.md)

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>创建非常简单的浏览器

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>下载网页

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP 文件

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>检索 Gopher 目录

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>使用"打开状态"回退

使用 WinInet 类时，可以使用应用程序的[CInternetSession](../mfc/reference/cinternetsession-class.md)对象的[OnStatusBack](../mfc/reference/cinternetsession-class.md#onstatuscallback)成员来检索状态信息。 如果派生自己的`CInternetSession`对象、重写`OnStatusCallback`和启用状态回调，MFC 将调用函数`OnStatusCallback`，并提供有关该 Internet 会话中所有活动的进度信息。

因为单个会话可能支持多个连接（在其生存期内，这些连接可能执行许多不同的操作），`OnStatusCallback`因此需要一种机制来识别具有特定连接或事务的每个状态更改。 该机制由 WinInet 支持类中许多成员函数提供的上下文 ID 参数提供。 此参数始终为**DWORD**类型，并且始终命名为*dwContext*。

分配给特定 Internet 对象的上下文仅用于标识`OnStatusCallback``CInternetSession`对象成员中的对象引起的活动。 调用接收`OnStatusCallback`多个参数;这些参数协同工作，告诉应用程序已为哪个事务和连接取得了哪些进展。

创建对象时`CInternetSession`，可以为构造函数指定*dwContext*参数。 `CInternetSession`本身不使用上下文 ID;因此，它不使用上下文 ID。相反，它将上下文 ID 传递给任何**InternetConnect**派生的对象，这些对象没有明确获取自己的上下文 ID。 反过来，如果不显式`CInternetConnection`指定其他上下文 ID，这些对象`CInternetFile`将上下文 ID 传递给它们创建的对象。 另一方面，如果确实指定您自己的特定上下文 ID、对象及其所做的任何工作都将与该上下文 ID 相关联。 您可以使用上下文标识标识在`OnStatusCallback`函数中为您提供的状态信息。

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>传输文件时显示进度信息

例如，如果编写一个应用程序创建与 FTP 服务器的连接以读取文件，并且还连接到 HTTP 服务器以获取 Web 页，则您将`CInternetSession`具有一个对象、两`CInternetConnection`个对象（一个对象，`CFtpSession`另一个`CHttpSession`对象是 ），以及两`CInternetFile`个对象（每个连接一个）。 如果为*dwContext*参数使用默认值，则无法区分`OnStatusCallback`指示 FTP 连接进度的调用和指示 HTTP 连接进度的调用。 如果指定*dwContext* ID，则可以稍后在 中`OnStatusCallback`测试该 ID，您将知道生成回调的操作。

## <a name="see-also"></a>另请参阅

[MFC 互联网编程基础知识](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 互联网扩展（WinInet）](../mfc/win32-internet-extensions-wininet.md)
