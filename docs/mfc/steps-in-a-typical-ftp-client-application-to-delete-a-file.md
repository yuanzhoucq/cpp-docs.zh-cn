---
title: 在典型 FTP 客户端应用程序中用于删除文件的步骤
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 5cd005908656f09028f95be38ee78c7887c2f223
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612441"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>在典型 FTP 客户端应用程序中用于删除文件的步骤

下表显示了在典型的删除文件的 FTP 客户端应用程序中可能执行的步骤。

|您的目标|采取的操作|效果|
|---------------|----------------------|-------------|
|FTP 会话开始。|创建[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|初始化 WinInet 并连接到服务器。|
|连接到 FTP 服务器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|返回[CFtpConnection](../mfc/reference/cftpconnection-class.md)对象。|
|检查以确保处于 FTP 服务器上的正确目录中。|使用[cftpconnection:: Getcurrentdirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)或[cftpconnection:: Getcurrentdirectoryasurl](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl)。|根据选择的成员函数，返回服务器上当前连接到的目录的名称或 URL。|
|更改为服务器上的新 FTP 目录。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|更改服务器上当前连接到的目录。|
|查找 FTP 目录中的第一个文件。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|查找第一个文件。 如果未找到文件，则返回 FALSE。|
|查找 FTP 目录中的下一个文件。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|查找下一个文件。 如果未找到文件，则返回 FALSE。|
|删除找到的文件`FindFile`或`FindNextFile`。|使用[cftpconnection:: Remove](../mfc/reference/cftpconnection-class.md#remove)，使用的文件的名称返回由`FindFile`或`FindNextFile`。|删除服务器上用于读取或写入的文件。|
|处理异常。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)类。|处理所有常见的 Internet 异常类型。|
|结束 FTP 会话。|释放[CInternetSession](../mfc/reference/cinternetsession-class.md)对象。|自动清理打开的文件句柄和连接。|

## <a name="see-also"></a>请参阅

[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
