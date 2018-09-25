---
title: Internet 客户端类的必备条件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e374305586db3c69a19194e866d5a03d3de91f4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402650"
---
# <a name="prerequisites-for-internet-client-classes"></a>Internet 客户端类的必备条件

Internet 客户端 （例如读取文件，） 执行某些操作具有必要的操作 （在此情况下，建立 Internet 连接）。 下表列出了一些客户端操作的先决条件。

### <a name="general-internet-url-ftp-gopher-or-http"></a>常规 Internet URL （FTP、 Gopher 或 HTTP）

|操作|必备组件|
|------------|------------------|
|建立连接。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)建立 Internet 客户端应用程序的基础。|
|打开 URL。|建立连接。 调用[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。 `OpenURL`函数返回的只读资源对象。|
|读取 URL 数据。|打开该 URL。 调用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|
|设置 Internet 选项。|建立连接。 调用[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)。|
|设置状态信息调用的函数。|建立连接。 调用[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)。 重写[CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)以处理调用。|

### <a name="ftp"></a>FTP

|操作|必备组件|
|------------|------------------|
|建立 FTP 连接。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)来创建[CFtpConnection](../mfc/reference/cftpconnection-class.md)对象。|
|找到的第一个资源。|建立 FTP 连接。 创建[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)对象。 调用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|
|枚举所有可用资源。|找到的第一个文件。 调用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)直到其返回 FALSE。|
|打开 FTP 文件。|建立 FTP 连接。 调用[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)以创建并打开[CInternetFile](../mfc/reference/cinternetfile-class.md)对象。|
|读取 FTP 文件。|打开 FTP 文件具有读取访问权限。 调用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|
|对 FTP 文件写入。|打开 FTP 文件具有写访问权限。 调用[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)。|
|更改服务器上的客户端的目录。|建立 FTP 连接。 调用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|
|检索服务器上的客户端的当前目录。|建立 FTP 连接。 调用[cftpconnection:: Getcurrentdirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)。|

### <a name="http"></a>HTTP

|操作|必备组件|
|------------|------------------|
|建立 HTTP 连接。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[cinternetsession:: Gethttpconnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)来创建[CHttpConnection](../mfc/reference/chttpconnection-class.md)对象。|
|打开 HTTP 文件。|建立 HTTP 连接。 调用[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)来创建[CHttpFile](../mfc/reference/chttpfile-class.md)对象。 调用[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)。 调用[CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest)。|
|读取 HTTP 文件。|打开 HTTP 文件。 调用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|
|获取有关 HTTP 请求的信息。|建立 HTTP 连接。 调用[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)来创建[CHttpFile](../mfc/reference/chttpfile-class.md)对象。 调用[CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo)。|

### <a name="gopher"></a>gopher

|操作|必备组件|
|------------|------------------|
|建立 gopher 连接。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[cinternetsession:: Getgopherconnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)来创建[CGopherConnection](../mfc/reference/cgopherconnection-class.md)。|
|在当前目录中查找第一个文件。|建立 gopher 连接。 创建[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)对象。 调用[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)来创建[CGopherLocator](../mfc/reference/cgopherlocator-class.md)对象。 传递到定位符[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)。 调用[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)以获取文件的定位符，如果需要更高版本。|
|枚举可用的所有文件。|找到的第一个文件。 调用[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)直到其返回 FALSE。|
|打开 gopher 文件。|建立 gopher 连接。 创建与 gopher 定位符[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)或查找使用定位符[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)。 调用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|
|读取 gopher 文件。|打开 gopher 文件。 使用[CGopherFile](../mfc/reference/cgopherfile-class.md)。|

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[用于创建 Internet 客户端应用程序的 MFC 类](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
