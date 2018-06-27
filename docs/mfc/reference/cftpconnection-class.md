---
title: CFtpConnection 类 |Microsoft 文档
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
ms.openlocfilehash: 303e89cd00091d8427bdb1d6e36c9a85b7aa5100
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952948"
---
# <a name="cftpconnection-class"></a>CFtpConnection 类
管理与 Internet 服务器的 FTP 连接，并允许该服务器上的目录和文件的直接操作。  
  
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
|[CFtpConnection::CreateDirectory](#createdirectory)|在服务器上创建目录。|  
|[Cftpconnection:: Getcurrentdirectory](#getcurrentdirectory)|获取此连接的当前目录。|  
|[Cftpconnection:: Getcurrentdirectoryasurl](#getcurrentdirectoryasurl)|获取作为 URL 的此连接的当前目录。|  
|[CFtpConnection::GetFile](#getfile)|连接的服务器中获取的文件|  
|[CFtpConnection::OpenFile](#openfile)|打开连接的服务器上的文件。|  
|[CFtpConnection::PutFile](#putfile)|将服务器上的文件。|  
|[Cftpconnection:: Remove](#remove)|从服务器中删除文件。|  
|[CFtpConnection::RemoveDirectory](#removedirectory)|从服务器中删除指定的目录。|  
|[CFtpConnection::Rename](#rename)|重命名服务器上的文件。|  
|[Cftpconnection:: Setcurrentdirectory](#setcurrentdirectory)|设置当前的 FTP 目录。|  
  
## <a name="remarks"></a>备注  
 FTP 是三个 Internet 服务识别的 MFC WinInet 类之一。  
  
 若要与 FTP Internet 服务器通信，必须先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后创建`CFtpConnection`对象。 切勿创建`CFtpConnection`直接对象; 相反，调用[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，这将创建`CFtpConnection`对象，并将指针返回到它。  
  
 若要了解有关如何`CFtpConnection`工作与其他 MFC Internet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。 有关与其他支持的两个通信的服务、 HTTP 和 gopher，请参阅类详细信息[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。  
  
## <a name="example"></a>示例  
  请参阅中的示例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)类概述。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>要求  
 **标头：** afxinet.h  
  
##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection  
 此成员函数调用以构造`CFtpConnection`对象。  
  
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
 指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 *hConnected*  
 当前的 Internet 会话的 Windows 句柄。  
  
 *pstrServer*  
 指向包含 FTP 服务器名称的字符串的指针。  
  
 *dwContext*  
 操作上下文标识符。 *dwContext*标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 对象和做的任何工作将与该上下文 id。  
  
 *pstrUserName*  
 指向以 null 结尾的字符串，指定要登录的用户的名称。 如果**NULL**，默认值是匿名的。  
  
 *pstrPassword*  
 指向一个以 null 结尾的字符串，指定要用于登录的密码的指针。 如果这两个*pstrPassword*和*pstrUserName*是**NULL**，默认匿名密码是用户的电子邮件名称。 如果*pstrPassword*是**NULL** （或空字符串），但*pstrUserName*不**NULL**，使用空白密码。 下表描述的四个可能的设置的行为*pstrUserName*和*pstrPassword*:  
  
|*pstrUserName*|*pstrPassword*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|"匿名"|用户的电子邮件名称|  
|非- **NULL**字符串|**NULL**或""|*pstrUserName*|" "|  
|**NULL**非**NULL**字符串|**错误**|**错误**||  
|非- **NULL**字符串|非- **NULL**字符串|*pstrUserName*|*pstrPassword*|  
  
 *nPort*  
 一个数字，标识要使用服务器上的 TCP/IP 端口。  
  
 *bPassive*  
 为此 FTP 会话指定被动还是主动模式。 如果设置为**TRUE**，它将设置 Win32 API *dwFlag*到**INTERNET_FLAG_PASSIVE**。  
  
### <a name="remarks"></a>备注  
 切勿创建`CFtpConnection`直接对象。 而应调用[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，这将创建**CFptConnection**对象。  
  
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
  
- **CmdRespNone**预期无响应。  
  
- **CmdRespRead**预期响应。  
  
 *dwFlags*  
 包含控制此函数的标志的值。 完整列表，请参阅[FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133)。  
  
 *dwContext*  
 指向一个值的指针，该值包含用于在回调中标识应用程序上下文的应用程序定义的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133)函数，如 Windows SDK 中所述。  
  
 如果发生错误，则 MFC 会引发类型的异常[CInternetException](../../mfc/reference/cinternetexception-class.md)。  
  
##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory  
 调用此成员函数可连接的服务器上创建一个目录。  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含要创建的目录的名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Windows 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 使用`GetCurrentDirectory`以确定此连接到服务器的当前工作目录。 不要假定该远程系统具有连接你到根目录。  
  
 `pstrDirName`参数可以是部分或完全限定的文件名相对于当前目录。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `CreateDirectory` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
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
 对将收到的目录名称的字符串的引用。  
  
 *pstrDirName*  
 指向将收到的目录名称的字符串的指针。  
  
 *lpdwLen*  
 指向一个 dword 值，包含以下信息的链接：  
  
|||  
|-|-|  
|条目|引用的缓冲区的大小*pstrDirName*。|  
|返回时|存储到的字符数*pstrDirName*。 如果成员函数将失败并返回 ERROR_INSUFFICIENT_BUFFER，然后*lpdwLen*包含的应用程序必须分配为了接收字符串的字节数。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 若要改为获取作为 URL 的目录名称，请调用[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。  
  
 参数*pstrDirName*或*strDirName*可以是相对于当前目录任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetCurrentDirectory` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
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
 对将收到的目录名称的字符串的引用。  
  
 *pstrDirName*  
 指向将收到的目录名称的字符串的指针。  
  
 *lpdwLen*  
 指向一个 dword 值，包含以下信息的链接：  
  
|||  
|-|-|  
|条目|引用的缓冲区的大小*pstrDirName*。|  
|返回时|存储到的字符数*pstrDirName*。 如果成员函数将失败并返回 ERROR_INSUFFICIENT_BUFFER，然后*lpdwLen*包含的应用程序必须分配为了接收字符串的字节数。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `GetCurrentDirectoryAsURL` 行为与相同[GetCurrentDirectory](#getcurrentdirectory)  
  
 参数*strDirName*可以是相对于当前目录任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetCurrentDirectoryAsURL` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
##  <a name="getfile"></a>  CFtpConnection::GetFile  
 调用此成员函数可从 FTP 服务器获取文件并将其存储在本地计算机上。  
  
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
 指向以 null 结尾的字符串，包含要从 FTP 服务器中检索的文件的名称的指针。  
  
 *pstrLocalFile*  
 指向包含要在本地系统上创建的文件的名称的以 null 结尾的字符串的指针。  
  
 *bFailIfExists*  
 指示是否文件名称可能已使用的现有文件。 如果本地文件名已存在，并且此参数是**TRUE**，`GetFile`失败。 否则为`GetFile`将会删除该文件的现有副本。  
  
 *dwAttributes*  
 指示的文件的属性。 这可以是以下 FILE_ATTRIBUTE_ * 标志的任意组合。  
  
-   FILE_ATTRIBUTE_ARCHIVE 文件是一个存档文件。 应用程序使用此特性标记的备份或删除的文件。  
  
-   压缩 FILE_ATTRIBUTE_COMPRESSED 文件或目录。 对于文件，压缩意味着所有文件中的数据进行压缩。 对于目录，压缩是新创建的文件和子目录的默认值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 文件是一个目录。  
  
-   FILE_ATTRIBUTE_NORMAL 文件没有设置任何其他属性。 此属性是单独使用时才有效。 所有其他文件特性重写 FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN 文件隐藏。 它是不包括在普通的目录列表。  
  
-   FILE_ATTRIBUTE_READONLY 文件具有只读属性。 应用程序可以读取该文件，但无法向其中写入或删除它。  
  
-   FILE_ATTRIBUTE_SYSTEM 该文件的一部分或操作系统被以独占方式使用。  
  
-   FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 仅当绝对必要，应用程序应写入到文件。 大部分文件的数据保留在内存中而不刷新到媒体因为该文件将很快被删除。  
  
 *dwFlags*  
 指定在其下传输发生的条件。 此参数可以为任何*dwFlags*值中所述[FtpGetFile](http://msdn.microsoft.com/library/windows/desktop/aa384157) Windows SDK 中。  
  
 *dwContext*  
 文件检索上下文标识符。 请参阅**备注**有关详细信息*dwContext*。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `GetFile` 是一个高级例程处理所有关联从 FTP 服务器读取文件并将其存储在本地的系统开销。 应用程序，只能检索文件的数据，或需要关闭控制文件传输，应使用`OpenFile`和[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)相反。  
  
 如果*dwFlags*也是 FILE_TRANSFER_TYPE_ASCII，转换后的文件数据，则会将控件和格式设置为 Windows 的等效字符。 默认传输是二进制模式，其中文件下载的相同的格式存储在服务器上。  
  
 同时*pstrRemoteFile*和*pstrLocalFile*可以是相对于当前目录任一部分限定的文件名或完全限定的。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `GetFile` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
 重写*dwContext*默认可为你选择的值设置的上下文标识符。 上下文标识符是与此特定操作的关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供有关用于标识的操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="openfile"></a>  CFtpConnection::OpenFile  
 调用此成员函数以打开位于用于读取或写入的 FTP 服务器上的文件。  
  
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
 确定将如何访问该文件。 可以 GENERIC_READ 或 GENERIC_WRITE，但不是两个。  
  
 *dwFlags*  
 指定在其下后续传输发生的条件。 这可以是任何 FTP_TRANSFER_ * 以下常量：  
  
-   FTP_TRANSFER_TYPE_ASCII 文件传输使用 FTP ASCII （A 类型） 传输方法。 将控件并为本地等效值的格式设置信息。  
  
-   FTP_TRANSFER_TYPE_BINARY 文件传输使用 FTP's 映像 (类型 I) 传输方法的数据。 存在完全相同的文件传输数据，不进行任何更改。 这是默认传输方法。  
  
 *dwContext*  
 打开的文件上下文标识符。 请参阅**备注**有关详细信息*dwContext*。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `OpenFile` 应在以下情况下使用：  
  
-   应用程序需要以进行发送和创建作为 FTP 服务器上的文件，但数据不是本地文件中的数据。 一次`OpenFile`打开一个文件，应用程序使用[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)将 FTP 文件数据发送到服务器。  
  
-   应用程序必须从服务器检索文件，并将其放入应用程序控制的内存，而不是写入磁盘。 应用程序使用[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)后使用`OpenFile`打开文件。  
  
-   应用程序需要精细的控制的文件传输级别。 例如，应用程序可能希望显示进度控件指示下载文件时的文件传输状态的进度。  
  
 在调用`OpenFile`和直到调用`CInternetConnection::Close`，只能调用应用程序[cinternetfile:: Read](../../mfc/reference/cinternetfile-class.md#read)， [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)， `CInternetConnection::Close`，或[Cftpfilefind:: Findfile](../../mfc/reference/cftpfilefind-class.md#findfile)。 对同一 FTP 会话其他 FTP 函数的调用将失败，并且将错误代码设置为 FTP_ETRANSFER_IN_PROGRESS。  
  
 *PstrFileName*参数可以为任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `OpenFile` 在使用它之前将转换到的相应字符的目录名称分隔符。  
  
 重写*dwContext*默认可为你选择的值设置的上下文标识符。 上下文标识符是与此特定操作的关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供有关用于标识的操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="putfile"></a>  CFtpConnection::PutFile  
 调用此成员函数以存储 FTP 服务器上的文件。  
  
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
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `PutFile` 是处理所有与存储 FTP 服务器上的文件关联的操作的高级例程。 应用程序，只发送数据，或需要进一步控制文件传输，应使用[OpenFile](#openfile)和[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)。  
  
 重写`dwContext`默认可为你选择的值设置的上下文标识符。 上下文标识符是与此特定操作的关联`CFtpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供有关用于标识的操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="remove"></a>  Cftpconnection:: Remove  
 调用此成员函数以从已连接的服务器中删除指定的文件。  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>参数  
 *pstrFileName*  
 指向包含要删除的文件名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrFileName*参数可以为任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 **删除**函数将转换为相应字符的目录名称分隔符，在使用之前。  
  
##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory  
 调用此成员函数以从已连接的服务器中删除指定的目录。  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含要删除的目录的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 使用[GetCurrentDirectory](#getcurrentdirectory)以确定服务器的当前工作目录。 不要假定该远程系统具有连接你到根目录。  
  
 *PstrDirName*参数可以是相对于当前目录的任一部分或完全限定的文件名。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `RemoveDirectory` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
##  <a name="rename"></a>  CFtpConnection::Rename  
 调用此成员函数以重命名已连接的服务器上的指定的文件。  
  
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
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrExisting*和*pstrNew*参数可以是任一部分限定的文件名相对于当前目录或完全限定。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 **重命名**在使用之前将转换为相应字符的目录名称分隔符。  
  
##  <a name="setcurrentdirectory"></a>  Cftpconnection:: Setcurrentdirectory  
 调用此成员函数可更改为 FTP 服务器上的不同目录。  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>参数  
 *pstrDirName*  
 指向包含的目录名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 *PstrDirName*参数可以是相对于当前目录的任一部分或完全限定的文件名。 反斜杠 (\\) 或正斜杠 （/） 可用作其中任一名称的目录分隔符。 `SetCurrentDirectory` 在使用之前，将转换为相应字符的目录名称分隔符。  
  
 使用[GetCurrentDirectory](#getcurrentdirectory)以确定 FTP 服务器的当前工作目录。 不要假定该远程系统具有连接你到根目录。  
  
## <a name="see-also"></a>请参阅  
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
