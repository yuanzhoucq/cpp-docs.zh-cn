---
title: "WinInet 基础知识 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnStatusCallback 方法"
  - "WinInet 类, 关于 WinInet 类"
  - "WinInet 类, 显示进度"
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WinInet 基础知识
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 WinInet 添加 FTP 支持以从应用程序内部下载和上载文件。  当您搜索并下载文件时，可以重写 [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) 和使用 `dwContext` 参数来提供进度信息给用户。  
  
 本章包含下列主题：  
  
-   [创建一个非常简单的浏览器](#_core_create_a_very_simple_browser)  
  
-   [下载一个网页](#_core_download_a_web_page)  
  
-   [FTP 文件](#_core_ftp_a_file)  
  
-   [检索 Gopher 目录](#_core_retrieve_a_gopher_directory)  
  
-   [当传输文件时，显示进度信息](#_core_display_progress_information_while_transferring_files)  
  
 下面代码的摘要演示如何创建一个简单的浏览器，下载一个网页、FTP文件和搜索 gopher 文件。  它们并不意味作为完全示例，也不是所有包含异常处理。  
  
 有关 WinInet 的详细信息，请参阅 [Win32 Internet 扩展 \(\/Ze WinInet\)](../mfc/win32-internet-extensions-wininet.md)。  
  
##  <a name="_core_create_a_very_simple_browser"></a> 创建一个非常简单的浏览器  
 [!CODE [NVC_MFCWinInet#1](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCWinInet#1)]  
  
##  <a name="_core_download_a_web_page"></a> 下载一个网页  
 [!CODE [NVC_MFCWinInet#2](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCWinInet#2)]  
  
##  <a name="_core_ftp_a_file"></a> FTP 文件  
 [!CODE [NVC_MFCWinInet#3](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCWinInet#3)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> 检索 Gopher 目录  
 [!CODE [NVC_MFCWinInet#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCWinInet#4)]  
  
## 使用 OnStatusCallback  
 当使用 WinInet 类时，可以使用应用程序的 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象的 [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) 成员检索状态信息。  如果派生您自己的 `CInternetSession` 对象，请重写 `OnStatusCallback`，并启用状态回调，MFC 将调用具有关于所有在此 Internet 会话中的进度信息的 `OnStatusCallback` 函数。  
  
 由于单一会话可能支持多个连接（它们的生存期内，可以执行多个明显不同的操作\)， `OnStatusCallback` 需要一种机制来标识与特定连接或事务中的每种状态更改。  通过给定的上下文 ID 参数提供机制给许多在 WinInet 支持类的成员函数。  此参数始终为 `DWORD` 类型并始终名为 `dwContext`。  
  
 上下文分配给特定 Internet 对象仅用于标识活动，该对象引起在 `CInternetSession` 对象的 `OnStatusCallback` 成员。  对 `OnStatusCallback` 调用接收多个参数；这些参数共同工作以告知应用程序哪些进度取得事务和连接。  
  
 当您创建 `CInternetSession` 对象时，您可以指定一个 `dwContext` 参数给构造函数。  `CInternetSession` 不使用 ID 上下文，相反它传递上下文 ID 给任意的 **InternetConnection**\- 未明确获取上下文 ID 的派生对象。  反过来，如果不显式指定一个不同的上下文 ID，他们创建这些 `CInternetConnection` 对象将传递上下文 ID 伴随 `CInternetFile` 对象。  另一方面如果您指定特定的上下文 ID，该对象和所有工作将与该上下文 ID 相联系。  可以使用上下文 ID 标识在 `OnStatusCallback` 函数中提供了什么状态信息。  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> 当传输文件时，显示进度信息  
 例如，如果您在编写创建一个与 FTP 服务器连接来读取文件并也连接到 HTTP 服务器获取网页的应用程序，则将具有一个 `CInternetSession` 对象、两个 `CInternetConnection` 对象 \(一种是 **CFtpSession**，而所有其他为 **CHttpSession** \) 和两个 `CInternetFile` 对象 \(每个连接一个\)。  如果为 `dwContext` 参数使用了默认值，您无法分清在指示 FTP 连接的进度与指示调用 HTTP 连接进度的 `OnStatusCallback` 调用的区别。  如果指定一个 `dwContext` ID，可以在 `OnStatusCallback` 后测试，您将知道哪些操作产生回调。  
  
## 请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)