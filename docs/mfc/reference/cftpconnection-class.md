---
title: CFtpConnection 类
ms.date: 08/29/2019
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
ms.openlocfilehash: 94ee4cb938ee061470282eb2f08a94d83c908805
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177281"
---
# <a name="cftpconnection-class"></a>CFtpConnection 类

管理与 Internet 服务器的 FTP 连接, 并允许直接操作该服务器上的目录和文件。

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
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|获取此连接的当前目录。|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|获取此连接的当前目录作为 URL。|
|[CFtpConnection::GetFile](#getfile)|从连接的服务器中获取文件|
|[CFtpConnection::OpenFile](#openfile)|打开连接的服务器上的文件。|
|[CFtpConnection::PutFile](#putfile)|将文件放在服务器上。|
|[CFtpConnection::Remove](#remove)|从服务器中删除文件。|
|[CFtpConnection::RemoveDirectory](#removedirectory)|从服务器中删除指定的目录。|
|[CFtpConnection::Rename](#rename)|重命名服务器上的文件。|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|设置当前 FTP 目录。|

## <a name="remarks"></a>备注

FTP 是 MFC WinInet 类识别的三个 Internet 服务之一。

若要与 FTP Internet 服务器通信, 必须先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例, 然后创建`CFtpConnection`对象。 永远不会直接`CFtpConnection`创建对象; 而是调用[CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` , 这将创建对象并返回指向该对象的指针。

若要了解有关如何`CFtpConnection`使用其他 MFC Internet 类的详细信息, 请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。 有关与其他两个受支持的服务进行通信的详细信息, 请参阅[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)类。

## <a name="example"></a>示例

  请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)类概述中的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>要求

**标头:** afxinet。h

##  <a name="cftpconnection"></a>CFtpConnection:: CFtpConnection

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

*pSession*<br/>
指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

*hConnected*<br/>
当前 Internet 会话的 Windows 句柄。

*pstrServer*<br/>
指向包含 FTP 服务器名称的字符串的指针。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识由[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)返回的操作的状态信息。 默认值设置为 1;但是, 您可以显式分配操作的特定上下文 ID。 对象及其执行的所有工作都将与该上下文 ID 相关联。

*pstrUserName*<br/>
指向以 null 结尾的字符串的指针, 该字符串指定要登录的用户的名称。 如果为 NULL, 则默认值为 anonymous。

*pstrPassword*<br/>
指向以 null 结尾的字符串的指针, 该字符串指定用于登录的密码。 如果*pstrPassword*和*PSTRUSERNAME*都为 NULL, 则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 null (或空字符串), 但*PSTRUSERNAME*不为 null, 则使用空密码。 下表描述了*pstrUserName*和*pstrPassword*的四个可能设置的行为:

|*pstrUserName*|*pstrPassword*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或 ""|NULL 或 ""|匿名|用户的电子邮件名称|
|非空字符串|NULL 或 ""|*pstrUserName*|" "|
|NULL 非空字符串|错误|错误||
|非空字符串|非空字符串|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
一个数字, 用于标识服务器上要使用的 TCP/IP 端口。

*bPassive*<br/>
为此 FTP 会话指定被动或主动模式。 如果设置为 TRUE, 则会将 Win32 API *dwFlag*设置为 INTERNET_FLAG_PASSIVE。

### <a name="remarks"></a>备注

永远不会直接`CFtpConnection`创建对象。 请改[为调用 CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), 这将`CFptConnection`创建对象。

##  <a name="command"></a>CFtpConnection:: 命令

向 FTP 服务器直接发送命令。

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pszCommand*<br/>
指向包含待发送命令的字符串的指针。

*eResponse*<br/>
指定 FTP 服务器是否需要响应。 可以是以下值之一：

- `CmdRespNone`不需要响应。
- `CmdRespRead`应为响应。
- `CmdRespWrite`不使用。

CmdResponseType 是*afxinet.h*中定义的 CFtpConnection 的成员。

*dwFlags*<br/>
包含控制此函数的标志的值。 有关完整列表, 请参阅[getdcbrushcolor](/windows/win32/api/wininet/nf-wininet-ftpcommandw)。

*dwContext*<br/>
指向一个值的指针，该值包含用于在回调中标识应用程序上下文的应用程序定义的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟[getdcbrushcolor](/windows/win32/api/wininet/nf-wininet-ftpcommandw)函数的功能, 如 Windows SDK 中所述。

如果发生错误, MFC 将引发类型为[CInternetException](../../mfc/reference/cinternetexception-class.md)的异常。

##  <a name="createdirectory"></a>CFtpConnection:: CreateDirectory

调用此成员函数在连接的服务器上创建目录。

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*pstrDirName*<br/>
指向字符串的指针, 该字符串包含要创建的目录的名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Windows 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

使用`GetCurrentDirectory`确定此与服务器的连接的当前工作目录。 不要假设远程系统已将你连接到根目录。

`pstrDirName`参数可以是部分或完全限定的文件名 (相对于当前目录)。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `CreateDirectory`使用之前, 将目录名称分隔符转换为相应的字符。

##  <a name="getcurrentdirectory"></a>CFtpConnection:: GetCurrentDirectory

调用此成员函数以获取当前目录的名称。

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>参数

*strDirName*<br/>
对将接收目录名称的字符串的引用。

*pstrDirName*<br/>
指向将接收目录名称的字符串的指针。

*lpdwLen*<br/>
一个指向 DWORD 的指针, 其中包含以下信息:

|||
|-|-|
|输入时|*PstrDirName*引用的缓冲区大小。|
|返回时|存储在*pstrDirName*中的字符数。 如果成员函数失败并且返回 ERROR_INSUFFICIENT_BUFFER, 则*lpdwLen*包含应用程序为了接收字符串而必须分配的字节数。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

若要改为获取目录名称作为 URL, 请调用[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。

参数*pstrDirName*或*strDirName*可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `GetCurrentDirectory`使用之前, 将目录名称分隔符转换为相应的字符。

##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection:: GetCurrentDirectoryAsURL

调用此成员函数以获取当前目录的名称作为 URL。

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>参数

*strDirName*<br/>
对将接收目录名称的字符串的引用。

*pstrDirName*<br/>
指向将接收目录名称的字符串的指针。

*lpdwLen*<br/>
一个指向 DWORD 的指针, 其中包含以下信息:

|||
|-|-|
|输入时|*PstrDirName*引用的缓冲区大小。|
|返回时|存储在*pstrDirName*中的字符数。 如果成员函数失败并且返回 ERROR_INSUFFICIENT_BUFFER, 则*lpdwLen*包含应用程序为了接收字符串而必须分配的字节数。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

`GetCurrentDirectoryAsURL`的行为与[GetCurrentDirectory](#getcurrentdirectory)相同

参数*strDirName*可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `GetCurrentDirectoryAsURL`使用之前, 将目录名称分隔符转换为相应的字符。

##  <a name="getfile"></a>CFtpConnection:: GetFile

调用此成员函数以从 FTP 服务器获取文件并将其存储在本地计算机上。

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

*pstrRemoteFile*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要从 FTP 服务器中检索的文件的名称。

*pstrLocalFile*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要在本地系统上创建的文件的名称。

*bFailIfExists*<br/>
指示文件名是否可能已被现有文件使用。 如果本地文件名已存在, 且此参数为 TRUE, `GetFile`则将失败。 否则, `GetFile`将删除文件的现有副本。

*dwAttributes*<br/>
指示文件的属性。 这可以是以下 FILE_ATTRIBUTE_ * 标志的任意组合。

- FILE_ATTRIBUTE_ARCHIVE 文件是存档文件。 应用程序使用此属性将文件标记为备份或删除。

- FILE_ATTRIBUTE_COMPRESSED 文件或目录已压缩。 对于文件, 压缩意味着文件中的所有数据都已压缩。 对于目录, 压缩是新创建的文件和子目录的默认值。

- FILE_ATTRIBUTE_DIRECTORY 该文件是一个目录。

- FILE_ATTRIBUTE_NORMAL 文件未设置其他属性。 仅当单独使用时, 此特性才有效。 所有其他文件属性都覆盖 FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN 文件处于隐藏状态。 它不会包含在普通目录列表中。

- FILE_ATTRIBUTE_READONLY 文件为只读。 应用程序可以读取该文件, 但不能写入或删除它。

- FILE_ATTRIBUTE_SYSTEM 文件是的一部分, 或者被操作系统独占使用。

- FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 应用程序只有在绝对必要时才应写入文件。 文件中的大部分数据都将保留在内存中, 而不会被刷新到媒体上, 因为此文件即将被删除。

*dwFlags*<br/>
指定发生传输的条件。 此参数可以是 Windows SDK 的[FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew)中所述的任何*dwFlags*值。

*dwContext*<br/>
文件检索的上下文标识符。 有关*dwContext*的详细信息, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

`GetFile`是一个高级例程, 处理与从 FTP 服务器读取文件并将其存储在本地有关的所有开销。 仅检索文件数据的应用程序或需要对文件传输进行关闭控制的应用程序应`OpenFile`使用和[CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) 。

如果*dwFlags*为 FILE_TRANSFER_TYPE_ASCII, 则文件数据的翻译还会将控件和格式字符转换为 Windows 等效项。 默认传输模式为二进制模式, 其中文件以存储在服务器上的相同格式下载。

*PstrRemoteFile*和*pstrLocalFile*都可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `GetFile`使用之前, 将目录名称分隔符转换为相应的字符。

重写*dwContext*默认值, 以将上下文标识符设置为你选择的值。 上下文标识符与`CFtpConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以提供用于标识该操作的状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

##  <a name="openfile"></a>CFtpConnection:: OpenFile

调用此成员函数以打开位于 FTP 服务器上的文件以进行读取或写入。

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pstrFileName*<br/>
指向字符串的指针, 该字符串包含要打开的文件的名称。

*dwAccess*<br/>
确定文件的访问方式。 可以是 GENERIC_READ 或 GENERIC_WRITE, 但不能同时为两者。

*dwFlags*<br/>
指定后续传输发生的条件。 这可以是以下任意 FTP_TRANSFER_ * 常量:

- FTP_TRANSFER_TYPE_ASCII 使用 FTP ASCII (类型 A) 传输方法传输文件。 将控件和格式设置信息转换为本地等效项。

- FTP_TRANSFER_TYPE_BINARY 文件使用 FTP 的图像 (类型 I) 传输方法传输数据。 文件将完全按原样传输数据, 无更改。 这是默认传输方法。

*dwContext*<br/>
用于打开文件的上下文标识符。 有关*dwContext*的详细信息, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

指向[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象的指针。

### <a name="remarks"></a>备注

`OpenFile`应在以下情况下使用:

- 应用程序包含需要在 FTP 服务器上以文件的形式发送和创建的数据, 但这些数据不在本地文件中。 打开`OpenFile`文件后, 应用程序将使用[CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)将 FTP 文件数据发送到服务器。

- 应用程序必须从服务器中检索文件并将其放入应用程序控制的内存中, 而不是将其写入磁盘。 应用程序使用[CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) `OpenFile`来打开文件。

- 应用程序需要对文件传输进行精细的控制。 例如, 应用程序可能希望在下载文件时显示进度控件以指示文件传输状态的进度。

在调用`OpenFile` `CInternetConnection::Close`和之前, 应用程序只能调用[CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read)、 [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)、 `CInternetConnection::Close`或[CFtpFileFind:: FindFile](../../mfc/reference/cftpfilefind-class.md#findfile)。 对同一 FTP 会话的其他 FTP 函数的调用将失败, 并将错误代码设置为 FTP_ETRANSFER_IN_PROGRESS。

*PstrFileName*参数可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `OpenFile`使用之前, 将目录名称分隔符转换为相应的字符。

重写*dwContext*默认值, 以将上下文标识符设置为你选择的值。 上下文标识符与`CFtpConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以提供用于标识该操作的状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

##  <a name="putfile"></a>CFtpConnection::P utFile

调用此成员函数以将文件存储在 FTP 服务器上。

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pstrLocalFile*<br/>
指向字符串的指针, 该字符串包含要从本地系统发送的文件的名称。

*pstrRemoteFile*<br/>
指向字符串的指针, 该字符串包含要在 FTP 服务器上创建的文件的名称。

*dwFlags*<br/>
指定发生文件传输的条件。 可以是[OpenFile](#openfile)中所述的任何 FTP_TRANSFER_ * 常量。

*dwContext*<br/>
用于放置文件的上下文标识符。 有关*dwContext*的详细信息, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

`PutFile`是一个高级例程, 用于处理与在 FTP 服务器上存储文件相关联的所有操作。 仅发送数据的应用程序或需要对文件传输更密切控制的应用程序应使用[OpenFile](#openfile)和[CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)。

重写`dwContext`默认值以将上下文标识符设置为你选择的值。 上下文标识符与`CFtpConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以提供用于标识该操作的状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

##  <a name="remove"></a>CFtpConnection:: Remove

调用此成员函数以从连接的服务器中删除指定的文件。

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>参数

*pstrFileName*<br/>
指向包含要删除的文件名的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

*PstrFileName*参数可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `Remove`函数将目录名称分隔符转换为相应的字符, 然后再使用它们。

##  <a name="removedirectory"></a>CFtpConnection:: RemoveDirectory

调用此成员函数以从连接的服务器中删除指定的目录。

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*pstrDirName*<br/>
指向字符串的指针, 该字符串包含要删除的目录。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

使用[GetCurrentDirectory](#getcurrentdirectory)确定服务器的当前工作目录。 不要假设远程系统已将你连接到根目录。

*PstrDirName*参数可以是相对于当前目录的部分或完全限定的文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `RemoveDirectory`使用之前, 将目录名称分隔符转换为相应的字符。

##  <a name="rename"></a>CFtpConnection:: Rename

调用此成员函数可重命名连接的服务器上的指定文件。

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>参数

*pstrExisting*<br/>
指向字符串的指针, 该字符串包含要重命名的文件的当前名称。

*pstrNew*<br/>
指向包含文件的新名称的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

*PstrExisting*和*pstrNew*参数可以是相对于当前目录或完全限定的部分限定文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `Rename`使用之前, 将目录名称分隔符转换为相应的字符。

##  <a name="setcurrentdirectory"></a>CFtpConnection:: SetCurrentDirectory

调用此成员函数以更改为 FTP 服务器上的其他目录。

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*pstrDirName*<br/>
指向包含目录名称的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

*PstrDirName*参数可以是相对于当前目录的部分或完全限定的文件名。 可以将反\\斜杠 () 或正斜杠 (/) 用作任意名称的目录分隔符。 `SetCurrentDirectory`使用之前, 将目录名称分隔符转换为相应的字符。

使用[GetCurrentDirectory](#getcurrentdirectory)确定 FTP 服务器的当前工作目录。 不要假设远程系统已将你连接到根目录。

## <a name="see-also"></a>请参阅

[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
