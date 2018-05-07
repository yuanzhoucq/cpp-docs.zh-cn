---
title: WinInet 基础知识 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38506d0b25918bbc9d70ec1801971b070d620bf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="wininet-basics"></a>WinInet 基础知识
你可以使用 WinInet 添加 FTP 支持，以下载并上载来自你的应用程序中的文件。 您可以重写[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)并用`dwContext`参数来搜索和下载文件，向用户提供进度信息。  
  
 本文包含以下主题：  
  
-   [创建非常简单的浏览器](#_core_create_a_very_simple_browser)  
  
-   [下载 Web 页](#_core_download_a_web_page)  
  
-   [Ftp 传输文件](#_core_ftp_a_file)  
  
-   [检索 Gopher 目录](#_core_retrieve_a_gopher_directory)  
  
-   [传输文件时显示进度信息](#_core_display_progress_information_while_transferring_files)  
  
 下面的代码摘自演示如何创建简单的浏览器，请下载网页，ftp 传输文件，并搜索 gopher 文件。 它们并不代表完整的示例并不是所有包含异常处理。  
  
 WinInet 的其他信息，请参阅[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)。  
  
##  <a name="_core_create_a_very_simple_browser"></a> 创建非常简单的浏览器  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a> 下载 Web 页  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a> Ftp 传输文件  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> 检索 Gopher 目录  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## <a name="use-onstatuscallback"></a>使用 OnStatusCallback  
 在使用 WinInet 类，你可以使用[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)的应用程序的成员[CInternetSession](../mfc/reference/cinternetsession-class.md)对象以检索状态信息。 如果派生你自己`CInternetSession`对象，请重写`OnStatusCallback`，并启用状态回调，MFC 将调用你`OnStatusCallback`函数使用该 Internet 会话中所有活动的进度信息。  
  
 因为单个会话可能支持 （其中，通过它们的生存期内可能执行许多不同的非重复操作） 的多个连接，`OnStatusCallback`需要一种机制来标识每个状态更改具有特定连接或事务。 该机制由赋予许多 WinInet 支持类中的成员函数的上下文 ID 参数提供。 此参数的类型始终是`DWORD`和总是被命名为`dwContext`。  
  
 分配给特定的 Internet 对象的上下文仅用于标识该对象导致活动`OnStatusCallback`的成员`CInternetSession`对象。 调用`OnStatusCallback`接收多个参数; 这些参数一起协作来告诉你的应用程序已为哪些事务和连接进行了哪些进度。  
  
 当你创建`CInternetSession`对象，你可以指定`dwContext`的构造函数参数。 `CInternetSession` 本身不使用的上下文 ID;相反，它传递到任何的上下文 ID **InternetConnection**-派生的对象的不显式获取自己的上下文 ID。 接下来，那些`CInternetConnection`对象将传递到沿上下文 ID`CInternetFile`对象他们创建如果不显式指定一个不同的上下文 id。 如果在另一方面，指定你自己的一个特定的上下文 ID、 对象和与其任何工作将与该上下文 id。 可以使用上下文 Id 来识别正在中向你提供状态信息你`OnStatusCallback`函数。  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> 传输文件时显示进度信息  
 例如，如果您编写的应用程序创建一个读取文件的 FTP 服务器与连接和与 HTTP 服务器以获取网页又连接，你将具有`CInternetSession`对象、 两个`CInternetConnection`对象 (一个将**CFtpSession**和另一个将是**CHttpSession**)，和两个`CInternetFile`对象 （一个用于每个连接）。 如果你使用的默认值`dwContext`参数，你将不能区分`OnStatusCallback`指示 FTP 连接和指示 HTTP 连接的进度调用的进度的调用。 如果指定`dwContext`ID，你可以更高版本测试是否在`OnStatusCallback`，你将知道哪些操作生成回调。  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

