---
title: CFtpConnection 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
dev_langs:
- C++
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c539504e7bb6e2b02b86d99c890ed5d6ecf1fc27
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217853"
---
# <a name="cftpconnection-class"></a>CFtpConnection 类
管理与 Internet 服务器的 FTP 连接，并允许直接操作目录和该服务器上的文件。  
  
## <a name="syntax"></a>语法  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFtpConnection::CFtpConnection](#cftpconnection)|构造 `CFtpConnection` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFtpConnection::Command](#command)|向 FTP 服务器直接发送命令。|  
|[CFtpConnection::CreateDirectory](#createdirectory)|在服务器上创建一个目录。|  
|[Cftpconnection:: Getcurrentdirectory](#getcurrentdirectory)|获取此连接的当前目录。|  
|[Cftpconnection:: Getcurrentdirectoryasurl](#getcurrentdirectoryasurl)|为此连接以 URL 形式获取当前目录。|  
|[CFtpConnection::GetFile](#getfile)|从连接的服务器获取的文件|  
|[CFtpConnection::OpenFile](#openfile)|打开连接的服务器上的文件。|  
|[CFtpConnection::PutFile](#putfile)|将放置在服务器上的文件。|  
|[Cftpconnection:: Remove](#remove)|从服务器中删除文件。|  
|[CFtpConnection::RemoveDirectory](#removedirectory)|从服务器中删除指定的目录。|  
|[CFtpConnection::Rename](#rename)|重命名服务器上的文件。|  
|[Cftpconnection:: Setcurrentdirectory](#setcurrentdirectory)|设置当前的 FTP 目录。|  
  
## <a name="remarks"></a>备注  
 FTP 是可识别的 MFC WinInet 类的三个 Internet 服务之一。  
  
 若要与 FTP Internet 服务器进行通信，必须首先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后创建`CFtpConnection`对象。 永远不会创建`CFtpConnection`直接对象; 而是调用[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，这将创建`CFtpConnection`对象并返回的指针。  
  
 若要详细了解如何`CFtpConnection`适用于其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 有关支持的其他两个与通信服务，HTTP 和 gopher，请参阅类详细信息[CHttpConnection](../../mfc/reference/chttpconnection-class.md)并[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。  
  
## <a name="example"></a>示例  
  请参阅中的示例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)类概述。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>要求  
 **标头：** afxinet.h  
  
##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection  
 调用此成员函数来构造`CFtpConnection`对象。  
  
```  
CFtpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CFtpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *pSession*  
 一个指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 *hConnected*  
 当前 Internet 会话的 Windows 句柄。  
  
 *pstrServer*  
 指向包含 FTP 服务器名称的字符串的指针。  
  
 *dwContext*  
 操作的上下文标识符。 *dwContext*标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 将与该上下文 id。 关联的对象以及它执行任何工作  
  
 *pstrUserName*  
 指向一个以 null 结尾的字符串，指定要登录的用户的名称。 如果为 NULL，则默认值是匿名的。  
  
 *pstrPassword*  
 一个指向一个以 null 结尾的字符串，指定要用于登录的密码。 如果这两个*pstrPassword*并*pstrUserName*为 NULL 时，默认匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL （或空字符串），但*pstrUserName*不为 NULL，则使用空密码。 下表描述了四个可能的设置的行为*pstrUserName*并*pstrPassword*:  
  
|*pstrUserName*|*pstrPassword*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|NULL 或""|NULL 或""|"匿名"|用户的电子邮件名称|  
|非 NULL 字符串|NULL 或""|*pstrUserName*|" "|  
|NULL 非空字符串|错误|错误||  
|非 NULL 字符串|非 NULL 字符串|*pstrUserName*|*pstrPassword*|  
  
 *nPort*  
 标识要在服务器上使用的 TCP/IP 端口号。  
  
 *bPassive*  
 为此 FTP 会话指定被动还是主动模式。 如果设置为 TRUE，则将设置 Win32 API *dwFlag* INTERNET_FLAG_PASSIVE 到。  
  
### <a name="remarks"></a>备注  
 永远不会创建`CFtpConnection`直接对象。 改为调用[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，这将创建`CFptConnection`对象。  
  
##  <a name="command"></a>  CFtpConnection::Command  
 向 FTP 服务器直接发送命令。  
  
```  
CInternetFile* Command(
    LPCTSTR pszCommand,  
    CmdResponseType eResponse = CmdRespNone,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 *pszCommand*  
 指向包含待发送命令的字符串的指针。  
  
 *eResponse*  
 确定是否预期从 FTP 服务器获得响应。 可以是以下值之一：  
  
- `CmdRespNone` 预期无响应。  
  
- `CmdRespRead` 预期响应。  
  
 *dwFlags*  
 包含控制此函数的标志的值。 有关完整列表，请参阅[FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda)。  
  
 *dwContext*  
 指向一个值的指针，该值包含用于在回调中标识应用程序上下文的应用程序定义的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda)函数，如 Windows SDK 中所述。  
  
 如果发生错误，则 MFC 会引发类型的异常[CInternetException](../../mfc/reference/cinternetexception-class.md)。  
  
##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory  
 调用此成员函数以连接的服务器上创建一个目录。  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含要创建的目录的名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Windows 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 使用`GetCurrentDirectory`来确定此连接到服务器的当前工作目录。 不要假定远程系统具有已您连接到的根目录。  
  
 `pstrDirName`参数可以是部分或完全限定的文件名相对于当前目录。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `CreateDirectory` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
##  <a name="getcurrentdirectory"></a>  Cftpconnection:: Getcurrentdirectory  
 调用此成员函数可获取当前目录的名称。  
  
```  
BOOL GetCurrentDirectory(CString& strDirName) const;  
  
BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>参数  
 *strDirName*  
 对将收到的目录的名称的字符串的引用。  
  
 *pstrDirName*  
 指向将接收的目录的名称的字符串的指针。  
  
 *lpdwLen*  
 指向一个 dword 值，其中包含以下信息的链接：  
  
|||  
|-|-|  
|条目|引用的缓冲区的大小*pstrDirName*。|  
|返回时|存储到的字符数*pstrDirName*。 如果此成员函数将失败并返回 ERROR_INSUFFICIENT_BUFFER，然后*lpdwLen*包含应用程序必须分配才能接收字符串的字节数。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 若要改为获取作为 URL 的目录名称，请调用[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。  
  
 参数*pstrDirName*或*strDirName*可以是相对于当前目录的任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetCurrentDirectory` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
##  <a name="getcurrentdirectoryasurl"></a>  Cftpconnection:: Getcurrentdirectoryasurl  
 调用此成员函数可获取当前目录的名称作为 URL。  
  
```  
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;  
  
BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>参数  
 *strDirName*  
 对将收到的目录的名称的字符串的引用。  
  
 *pstrDirName*  
 指向将接收的目录的名称的字符串的指针。  
  
 *lpdwLen*  
 指向一个 dword 值，其中包含以下信息的链接：  
  
|||  
|-|-|  
|条目|引用的缓冲区的大小*pstrDirName*。|  
|返回时|存储到的字符数*pstrDirName*。 如果此成员函数将失败并返回 ERROR_INSUFFICIENT_BUFFER，然后*lpdwLen*包含应用程序必须分配才能接收字符串的字节数。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `GetCurrentDirectoryAsURL` 行为与相同[GetCurrentDirectory](#getcurrentdirectory)  
  
 将参数*strDirName*可以是相对于当前目录的任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetCurrentDirectoryAsURL` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
##  <a name="getfile"></a>  CFtpConnection::GetFile  
 调用此成员函数以获取从 FTP 服务器的文件并将其存储在本地计算机上。  
  
```  
BOOL GetFile(
    LPCTSTR pstrRemoteFile,  
    LPCTSTR pstrLocalFile,  
    BOOL bFailIfExists = TRUE,  
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 *pstrRemoteFile*  
 指向包含要从 FTP 服务器检索文件的名称的以 null 结尾的字符串的指针。  
  
 *pstrLocalFile*  
 指向包含要在本地系统上创建的文件的名称的以 null 结尾的字符串的指针。  
  
 *bFailIfExists*  
 指示是否文件名称可能已使用的现有文件。 如果本地文件名称已存在，并且此参数为 TRUE，`GetFile`失败。 否则为`GetFile`将清除该文件的现有副本。  
  
 *dwAttributes*  
 指示文件的属性。 这可以是以下 FILE_ATTRIBUTE_ * 标志的任意组合。  
  
-   FILE_ATTRIBUTE_ARCHIVE 文件是一个存档文件。 应用程序使用此特性标记的备份或删除的文件。  
  
-   压缩 FILE_ATTRIBUTE_COMPRESSED 文件或目录。 对于文件，压缩意味着所有文件中的数据进行压缩。 对于目录，压缩是新创建的文件和子目录的默认值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 文件是一个目录。  
  
-   FILE_ATTRIBUTE_NORMAL 文件没有设置任何其他属性。 此属性是单独使用时才有效。 所有其他文件属性重写 FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN 文件被隐藏。 它并不是包含在普通的目录列表。  
  
-   FILE_ATTRIBUTE_READONLY 文件是只读的。 应用程序可以读取该文件，但不能向其中写入或删除它。  
  
-   该文件的一部分或由操作系统以独占方式使用 FILE_ATTRIBUTE_SYSTEM。  
  
-   FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 仅当绝对必要，应用程序应写入到文件。 大多数文件的数据保留在内存中而无需因为即将被删除的文件刷新到该媒体。  
  
 *dwFlags*  
 指定在其下传输发生的条件。 此参数可以是任一*dwFlags*值中所述[FtpGetFile](/windows/desktop/api/wininet/nf-wininet-ftpgetfilea) Windows SDK 中。  
  
 *dwContext*  
 文件检索上下文标识符。 请参阅**备注**有关详细信息*dwContext*。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `GetFile` 是处理所有从 FTP 服务器读取文件并将其本地存储与相关的高级例程。 应用程序，只检索文件数据，或者要求关闭控制文件传输，应使用`OpenFile`并[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)相反。  
  
 如果*dwFlags*也是 FILE_TRANSFER_TYPE_ASCII，文件数据的转换，则会将控件和格式设置为 Windows 等效项的字符。 默认传输是二进制模式下，其中此文件存储在服务器上下载相同的格式。  
  
 这两*pstrRemoteFile*并*pstrLocalFile*可以是相对于当前目录的任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetFile` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
 重写*dwContext*默认可为您选择的值设置的上下文标识符。 上下文标识符是否与此特定操作相关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="openfile"></a>  CFtpConnection::OpenFile  
 调用此成员函数以打开用于读取或写入 FTP 服务器上的文件。  
  
```  
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,  
    DWORD dwAccess = GENERIC_READ,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 *pstrFileName*  
 指向包含要打开的文件的名称的字符串的指针。  
  
 *dwAccess*  
 确定如何将访问该文件。 可以是 GENERIC_READ 或 generic_write 外，而不是两者。  
  
 *dwFlags*  
 指定后续传输发生的条件。 这可以是任何以下 FTP_TRANSFER_ * 常量：  
  
-   FTP_TRANSFER_TYPE_ASCII 文件传输使用 FTP ASCII （类型 A） 传输方法。 将控件并为本地等效项的格式设置信息。  
  
-   FTP_TRANSFER_TYPE_BINARY 文件传输使用 FTP's 映像 (类型 I) 传输方法的数据。 存在完全相同的文件传输数据，不进行任何更改。 这是默认传输方法。  
  
 *dwContext*  
 打开的文件上下文标识符。 请参阅**备注**有关详细信息*dwContext*。  
  
### <a name="return-value"></a>返回值  
 一个指向[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `OpenFile` 应在以下情况下使用：  
  
-   应用程序具有需要发送并创建为 FTP 服务器上的文件，但数据不是本地文件中的数据。 一次`OpenFile`打开一个文件，应用程序使用[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)将 FTP 文件数据发送到服务器。  
  
-   应用程序必须从服务器检索文件并将其放入应用程序控制的内存，而不是写入到磁盘。 应用程序使用[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)之后使用`OpenFile`以打开该文件。  
  
-   应用程序需要精细控制的文件传输。 例如，应用程序可能想要显示进度控件下载文件时指示进度的文件传输状态。  
  
 在调用`OpenFile`和之前调用`CInternetConnection::Close`，应用程序可以只调用[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)， [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)， `CInternetConnection::Close`，或[Cftpfilefind:: Findfile](../../mfc/reference/cftpfilefind-class.md#findfile)。 对同一个 FTP 会话其他 FTP 函数的调用将失败，并将错误代码设置为 FTP_ETRANSFER_IN_PROGRESS。  
  
 *PstrFileName*参数可以是任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `OpenFile` 然后再使用它将转换为相应的字符的目录名称分隔符。  
  
 重写*dwContext*默认可为您选择的值设置的上下文标识符。 上下文标识符是否与此特定操作相关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="putfile"></a>  CFtpConnection::PutFile  
 调用此成员函数来存储 FTP 服务器上的文件。  
  
```  
BOOL PutFile(
    LPCTSTR pstrLocalFile,  
    LPCTSTR pstrRemoteFile,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 *pstrLocalFile*  
 指向包含要从本地系统发送的文件的名称的字符串的指针。  
  
 *pstrRemoteFile*  
 指向包含要在 FTP 服务器上创建的文件的名称的字符串的指针。  
  
 *dwFlags*  
 指定在其下的文件传输发生的条件。 可以是任何中所述的 FTP_TRANSFER_ * 常量[OpenFile](#openfile)。  
  
 *dwContext*  
 放置文件的上下文标识符。 请参阅**备注**有关详细信息*dwContext*。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `PutFile` 是处理所有与存储 FTP 服务器上的文件关联的操作的高级例程。 应用程序，只发送的数据，或需要进一步控制文件传输，应使用[OpenFile](#openfile)并[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)。  
  
 重写`dwContext`默认可为您选择的值设置的上下文标识符。 上下文标识符是否与此特定操作相关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="remove"></a>  Cftpconnection:: Remove  
 调用此成员函数以从连接的服务器中删除指定的文件。  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>参数  
 *pstrFileName*  
 指向包含要删除的文件名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrFileName*参数可以是任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `Remove`函数将转换为相应的字符的目录名称分隔符，在使用之前。  
  
##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory  
 调用此成员函数以从连接的服务器中删除指定的目录。  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含要删除的目录的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 使用[GetCurrentDirectory](#getcurrentdirectory)以确定服务器的当前工作目录。 不要假定远程系统具有已您连接到的根目录。  
  
 *PstrDirName*参数可以是相对于当前目录的任一部分或完全限定的文件名。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `RemoveDirectory` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
##  <a name="rename"></a>  CFtpConnection::Rename  
 调用此成员函数以重命名连接的服务器上指定的文件。  
  
```  
BOOL Rename(
    LPCTSTR pstrExisting,  
    LPCTSTR pstrNew);
```  
  
### <a name="parameters"></a>参数  
 *pstrExisting*  
 指向包含要重命名的文件的当前名称的字符串的指针。  
  
 *pstrNew*  
 指向包含新文件名的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrExisting*并*pstrNew*参数可以是任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `Rename` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
##  <a name="setcurrentdirectory"></a>  Cftpconnection:: Setcurrentdirectory  
 调用此成员函数以将更改为 FTP 服务器上的不同目录。  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含的目录的名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrDirName*参数可以是相对于当前目录的任一部分或完全限定的文件名。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `SetCurrentDirectory` 在使用之前，将转换为相应的字符的目录名称分隔符。  
  
 使用[GetCurrentDirectory](#getcurrentdirectory)来确定 FTP 服务器的当前工作目录。 不要假定远程系统具有已您连接到的根目录。  
  
## <a name="see-also"></a>请参阅  
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
