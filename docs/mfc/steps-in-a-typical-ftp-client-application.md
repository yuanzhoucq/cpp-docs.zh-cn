---
title: 典型 FTP 客户端应用程序中的步骤 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ac1eef12a3f782f3ad9ba8a9bb526989876251e
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890213"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>典型 FTP 客户端应用程序中的步骤

典型 FTP 客户端应用程序创建[CInternetSession](../mfc/reference/cinternetsession-class.md)和一个[CFtpConnection](../mfc/reference/cftpconnection-class.md)对象。 请注意，这些 MFC WinInet 类并不实际控制代理类型设置;执行 IIS。

下表显示了可能会执行典型 FTP 客户端应用程序中的步骤。

|您的目标|采取的操作|效果|
|---------------|----------------------|-------------|
|FTP 会话开始。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|
|连接到 FTP 服务器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|返回[CFtpConnection](../mfc/reference/cftpconnection-class.md)对象。|
|更改为服务器上的新 FTP 目录。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|更改服务器上当前连接到的目录。|
|查找 FTP 目录中的第一个文件。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|查找第一个文件。 如果未找到文件，则返回 FALSE。|
|查找 FTP 目录中的下一个文件。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|查找下一个文件。 如果未找到文件，则返回 FALSE。|
|打开发现的文件`FindFile`或`FindNextFile`用于读取或写入。|使用[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)，使用的文件的名称返回由[FindFile](../mfc/reference/cftpfilefind-class.md#findfile)或[FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|打开服务器上用于读取或写入的文件。 返回[CInternetFile](../mfc/reference/cinternetfile-class.md)对象。|
|读取或写入到文件。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)或[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)。|读取或写入指定的字节，使用您提供的缓冲区数。|
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|
|结束 FTP 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
