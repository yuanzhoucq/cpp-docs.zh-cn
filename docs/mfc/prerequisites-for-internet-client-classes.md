---
title: Internet 客户端类的必备条件
ms.date: 11/04/2016
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
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619836"
---
# <a name="prerequisites-for-internet-client-classes"></a>Internet 客户端类的必备条件

Internet 客户端执行的某些操作（例如，读取文件）具有先决条件操作（在这种情况下，建立 Internet 连接）。 下表列出了一些客户端操作的先决条件。

### <a name="general-internet-url-ftp-gopher-or-http"></a>常规 Internet URL （FTP、Gopher 或 HTTP）

|操作|先决条件|
|------------|------------------|
|建立连接。|创建[CInternetSession](reference/cinternetsession-class.md)以建立 Internet 客户端应用程序的基础。|
|打开 URL。|建立连接。 调用[CInternetSession：： OpenURL](reference/cinternetsession-class.md#openurl)。 `OpenURL`函数返回一个只读资源对象。|
|读取 URL 数据。|打开 URL。 调用[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|设置 Internet 选项。|建立连接。 调用[CInternetSession：： SetOption](reference/cinternetsession-class.md#setoption)。|
|设置要使用状态信息调用的函数。|建立连接。 调用[CInternetSession：： EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback)。 重写[CInternetSession：： OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback)以处理调用。|

### <a name="ftp"></a>FTP

|操作|先决条件|
|------------|------------------|
|建立 FTP 连接。|创建[CInternetSession](reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[CInternetSession：： GetFtpConnection](reference/cinternetsession-class.md#getftpconnection)以创建一个[CFtpConnection](reference/cftpconnection-class.md)对象。|
|查找第一个资源。|建立 FTP 连接。 创建[CFtpFileFind](reference/cftpfilefind-class.md)对象。 调用[CFtpFileFind：： FindFile](reference/cftpfilefind-class.md#findfile)。|
|枚举所有可用资源。|查找第一个文件。 调用[CFtpFileFind：： FindNextFile](reference/cftpfilefind-class.md#findnextfile) ，直到它返回 FALSE。|
|打开 FTP 文件。|建立 FTP 连接。 调用[CFtpConnection：： OpenFile](reference/cftpconnection-class.md#openfile)以创建并打开[CInternetFile](reference/cinternetfile-class.md)对象。|
|读取 FTP 文件。|使用读取访问权限打开 FTP 文件。 调用[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|写入 FTP 文件。|打开具有写访问权限的 FTP 文件。 调用[CInternetFile：： Write](reference/cinternetfile-class.md#write)。|
|更改服务器上的客户端目录。|建立 FTP 连接。 调用[CFtpConnection：： SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory)。|
|检索服务器上客户端的当前目录。|建立 FTP 连接。 调用[CFtpConnection：： GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory)。|

### <a name="http"></a>HTTP

|操作|先决条件|
|------------|------------------|
|建立 HTTP 连接。|创建[CInternetSession](reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[CInternetSession：： GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection)以创建一个[CHttpConnection](reference/chttpconnection-class.md)对象。|
|打开 HTTP 文件。|建立 HTTP 连接。 调用[CHttpConnection：： OpenRequest](reference/chttpconnection-class.md#openrequest)以创建一个[CHttpFile](reference/chttpfile-class.md)对象。 调用[CHttpFile：： AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders)。 调用[CHttpFile：： SendRequest](reference/chttpfile-class.md#sendrequest)。|
|读取 HTTP 文件。|打开 HTTP 文件。 调用[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|获取有关 HTTP 请求的信息。|建立 HTTP 连接。 调用[CHttpConnection：： OpenRequest](reference/chttpconnection-class.md#openrequest)以创建一个[CHttpFile](reference/chttpfile-class.md)对象。 调用[CHttpFile：： QueryInfo](reference/chttpfile-class.md#queryinfo)。|

### <a name="gopher"></a>Gopher

|操作|先决条件|
|------------|------------------|
|建立 gopher 连接。|创建[CInternetSession](reference/cinternetsession-class.md)作为此 Internet 客户端应用程序的基础。 调用[CInternetSession：： GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection)以创建[CGopherConnection](reference/cgopherconnection-class.md)。|
|查找当前目录中的第一个文件。|建立 gopher 连接。 创建[CGopherFileFind](reference/cgopherfilefind-class.md)对象。 调用[CGopherConnection：： CreateLocator](reference/cgopherconnection-class.md#createlocator)以创建一个[CGopherLocator](reference/cgopherlocator-class.md)对象。 将定位符传递到[CGopherFileFind：： FindFile](reference/cgopherfilefind-class.md#findfile)。 调用[CGopherFileFind：： GetLocator](reference/cgopherfilefind-class.md#getlocator)以获取文件的定位符（如果以后需要）。|
|枚举所有可用的文件。|查找第一个文件。 调用[CGopherFileFind：： FindNextFile](reference/cgopherfilefind-class.md#findnextfile) ，直到它返回 FALSE。|
|打开 gopher 文件。|建立 gopher 连接。 使用[CGopherConnection：： CreateLocator](reference/cgopherconnection-class.md#createlocator)创建 gopher 定位符，或使用[CGopherFileFind：： GetLocator](reference/cgopherfilefind-class.md#getlocator)查找定位符。 调用[CGopherConnection：： OpenFile](reference/cgopherconnection-class.md#openfile)。|
|读取 gopher 文件。|打开 gopher 文件。 请使用[CGopherFile](reference/cgopherfile-class.md)。|

## <a name="see-also"></a>另请参阅

[Win32 Internet 扩展（WinInet）](win32-internet-extensions-wininet.md)<br/>
[用于创建 Internet 客户端应用程序的 MFC 类](mfc-classes-for-creating-internet-client-applications.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](writing-an-internet-client-application-using-mfc-wininet-classes.md)
