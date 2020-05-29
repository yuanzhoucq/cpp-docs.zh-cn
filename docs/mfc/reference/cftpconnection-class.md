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
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373778"
---
# <a name="cftpconnection-class"></a>CFtpConnection 类

管理与 Internet 服务器的 FTP 连接，并允许直接操作该服务器上的目录和文件。

## <a name="syntax"></a>语法

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CFtp 连接：：CFtp 连接](#cftpconnection)|构造 `CFtpConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFtp 连接：：命令](#command)|向 FTP 服务器直接发送命令。|
|[CFtp 连接：：创建目录](#createdirectory)|在服务器上创建目录。|
|[CFtp 连接：：获取当前目录](#getcurrentdirectory)|获取此连接的当前目录。|
|[CFtp 连接：：获取当前目录](#getcurrentdirectoryasurl)|获取此连接的当前目录作为 URL。|
|[CFtp 连接：获取文件](#getfile)|从连接的服务器获取文件|
|[CFtp 连接：：打开文件](#openfile)|在连接的服务器上打开文件。|
|[CFtp连接：:PutFile](#putfile)|将文件放在服务器上。|
|[CFtp 连接：：删除](#remove)|从服务器中删除文件。|
|[CFtp 连接：：删除目录](#removedirectory)|从服务器中删除指定的目录。|
|[CFtp 连接：：重命名](#rename)|重命名服务器上的文件。|
|[CFtp 连接：：设置当前目录](#setcurrentdirectory)|设置当前 FTP 目录。|

## <a name="remarks"></a>备注

FTP 是 MFC WinInet 类认可的三大互联网服务之一。

要与 FTP Internet 服务器通信，必须首先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例，然后创建`CFtpConnection`对象。 您从不直接创建`CFtpConnection`对象;相反，调用[CInternetSession：：GetFtpConnect](../../mfc/reference/cinternetsession-class.md#getftpconnection)，它`CFtpConnection`创建对象并返回指向它的指针。

要了解有关如何`CFtpConnection`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。 有关与其他两个受支持的服务 HTTP 和 gopher 通信的详细信息，请参阅[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)的类。

## <a name="example"></a>示例

  请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)类概述中的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 互联网连接](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtp 连接：：CFtp 连接

调用此成员函数以构造对象`CFtpConnection`。

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

*p 会话*<br/>
指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

*h 连接*<br/>
当前 Internet 会话的 Windows 句柄。

*pstrServer*<br/>
指向包含 FTP 服务器名称的字符串的指针。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识 CInternetSession 返回的操作的状态信息[：：onStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 默认值设置为 1;将默认值设置为 1但是，您可以显式为操作分配特定的上下文 ID。 对象及其执行的任何工作都将与该上下文 ID 相关联。

*pstrUser 名称*<br/>
指向 null 终止字符串的指针，该字符串指定要登录的用户的名称。 如果为 NULL，则默认值为匿名。

*pstr密码*<br/>
指向 null 终止字符串的指针，用于指定用于登录的密码。 如果*pstrPassword*和*pstrUserName*均为 NULL，则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL（或空字符串），但*pstrUserName*不是 NULL，则使用空白密码。 下表描述了*pstrUserName*和*pstrPassword*的四种可能设置的行为：

|*pstrUser 名称*|*pstr密码*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|用户的电子邮件名称|
|非 NULL 字符串|NULL 或""|*pstrUser 名称*|" "|
|NULL 非 NULL 字符串|ERROR|ERROR||
|非 NULL 字符串|非 NULL 字符串|*pstrUser 名称*|*pstr密码*|

*n波特*<br/>
标识要在服务器上使用的 TCP/IP 端口的数字。

*b被动*<br/>
为此 FTP 会话指定被动或主动模式。 如果设置为 TRUE，它将 Win32 API *dwFlag*设置为INTERNET_FLAG_PASSIVE。

### <a name="remarks"></a>备注

您从不直接创建`CFtpConnection`对象。 相反，调用[CInternetSession：：GetFtpConnect](../../mfc/reference/cinternetsession-class.md#getftpconnection)，这将`CFptConnection`创建对象。

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtp 连接：：命令

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
指定是否预期来自 FTP 服务器的响应。 可以是以下值之一：

- `CmdRespNone`预期不会响应。
- `CmdRespRead`预期会做出响应。
- `CmdRespWrite`未使用。

CmdResponseType 是 CFtpConnection 的成员，在*afxinet.h*中定义。

dwFlags**<br/>
包含控制此函数的标志的值。 有关完整列表，请参阅[FTP命令](/windows/win32/api/wininet/nf-wininet-ftpcommandw)。

*dwContext*<br/>
指向一个值的指针，该值包含用于在回调中标识应用程序上下文的应用程序定义的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟[FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)函数的功能，如 Windows SDK 中所述。

如果发生错误，MFC 将引发[CInternetException](../../mfc/reference/cinternetexception-class.md)类型的异常。

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtp 连接：：创建目录

调用此成员函数在连接的服务器上创建目录。

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*普斯特迪尔名称*<br/>
指向包含要创建的目录名称的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Windows 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

用于`GetCurrentDirectory`确定此连接到服务器的当前工作目录。 不要假定远程系统已将您连接到根目录。

参数`pstrDirName`可以是相对于当前目录的部分或完全限定的文件名。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `CreateDirectory`在使用目录名称分隔符之前，将其转换为相应的字符。

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtp 连接：：获取当前目录

调用此成员函数以获取当前目录的名称。

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>参数

*斯特迪尔名称*<br/>
对将接收目录名称的字符串的引用。

*普斯特迪尔名称*<br/>
指向将接收目录名称的字符串的指针。

*lpdwLen*<br/>
指向包含以下信息的 DWORD 的指针：

|||
|-|-|
|入场时|*pstrDirName*引用的缓冲区的大小。|
|返回时|存储到*pstrDirName*的字符数。 如果成员函数失败并返回ERROR_INSUFFICIENT_BUFFER，则*lpdwLen*包含应用程序必须分配的字节数才能接收字符串。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

要将目录名称作为 URL，请调用[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。

参数*pstrDirName*或*strDirName*可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `GetCurrentDirectory`在使用目录名称分隔符之前，将其转换为相应的字符。

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtp 连接：：获取当前目录

调用此成员函数以获取当前目录的名称作为 URL。

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>参数

*斯特迪尔名称*<br/>
对将接收目录名称的字符串的引用。

*普斯特迪尔名称*<br/>
指向将接收目录名称的字符串的指针。

*lpdwLen*<br/>
指向包含以下信息的 DWORD 的指针：

|||
|-|-|
|入场时|*pstrDirName*引用的缓冲区的大小。|
|返回时|存储到*pstrDirName*的字符数。 如果成员函数失败并返回ERROR_INSUFFICIENT_BUFFER，则*lpdwLen*包含应用程序必须分配的字节数才能接收字符串。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

`GetCurrentDirectoryAsURL`其活动与[GetCurrentDirectory](#getcurrentdirectory)相同

参数*strDirName*可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `GetCurrentDirectoryAsURL`在使用目录名称分隔符之前，将其转换为相应的字符。

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtp 连接：获取文件

调用此成员函数从 FTP 服务器获取文件并将其存储在本地计算机上。

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
指向从 FTP 服务器检索的文件名称的 null 端接字符串的指针。

*pstrlocalFile*<br/>
指向在本地系统上创建的文件名称的 null 端结束的字符串的指针。

*bFailIf存在*<br/>
指示现有文件是否已经使用文件名。 如果本地文件名已存在，并且此参数为 TRUE，`GetFile`则失败。 否则，`GetFile`将擦除文件的现有副本。

*dwAttributes*<br/>
指示文件的属性。 这可以是以下FILE_ATTRIBUTE_* 标志的任意组合。

- FILE_ATTRIBUTE_ARCHIVE 该文件是存档文件。 应用程序使用此属性标记文件以进行备份或删除。

- FILE_ATTRIBUTE_COMPRESSED文件或目录被压缩。 对于文件，压缩意味着文件中的所有数据被压缩。 对于目录，压缩是新创建的文件和子目录的默认值。

- FILE_ATTRIBUTE_DIRECTORY 该文件是目录。

- FILE_ATTRIBUTE_NORMAL 该文件没有其他属性集。 此属性仅在单独使用时有效。 所有其他文件属性将覆盖FILE_ATTRIBUTE_NORMAL：

- FILE_ATTRIBUTE_HIDDEN文件已隐藏。 它不包含在普通目录列表中。

- FILE_ATTRIBUTE_READONLY该文件是只读的。 应用程序可以读取文件，但不能写入或删除该文件。

- FILE_ATTRIBUTE_SYSTEM 该文件是 操作系统的一部分或由操作系统专门使用。

- FILE_ATTRIBUTE_TEMPORARY 该文件用于临时存储。 应用程序仅在绝对必要时才应写入文件。 文件的大部分数据保留在内存中，而不会刷新到介质，因为该文件将很快被删除。

dwFlags**<br/>
指定传输发生的条件。 此参数可以是 Windows SDK 中[FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew)中描述的任何*dwFlags*值。

*dwContext*<br/>
文件检索的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

`GetFile`是一种高级例程，用于处理与从 FTP 服务器读取文件并在本地存储文件相关的所有开销。 仅检索文件数据或需要严格控制文件传输的应用程序应使用`OpenFile` [CInternetFile：：改为读取](../../mfc/reference/cinternetfile-class.md#read)。

如果*dwFlags* FILE_TRANSFER_TYPE_ASCII，则文件数据的转换也会将控件和格式字符转换为 Windows 等效项。 默认传输是二进制模式，其中文件下载的格式与存储在服务器上的格式相同。

*pstrRemoteFile*和*pstrLocalFile*都可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `GetFile`在使用目录名称分隔符之前，将其转换为相应的字符。

覆盖*dwContext*默认值，将上下文标识符设置为您选择的值。 上下文标识符与其`CFtpConnection`[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession：：onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供标识该值的操作的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtp 连接：：打开文件

调用此成员函数打开位于 FTP 服务器上的文件以进行读取或写入。

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pstrFile名称*<br/>
指向包含要打开的文件名称的字符串的指针。

*dwAccess*<br/>
确定如何访问该文件。 可以是GENERIC_READ或GENERIC_WRITE，但不能同时使用这两者。

dwFlags**<br/>
指定后续传输发生的条件。 这可以是以下任何FTP_TRANSFER_* 常量：

- FTP_TRANSFER_TYPE_ASCII使用 FTP ASCII （类型 A） 传输方法传输文件。 将控件和格式信息转换为本地等效项。

- FTP_TRANSFER_TYPE_BINARY文件使用 FTP 的图像（类型 I）传输方法传输数据。 文件传输数据完全与它存在一样，没有更改。 这是默认传输方法。

*dwContext*<br/>
用于打开文件的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="return-value"></a>返回值

指向[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象的指针。

### <a name="remarks"></a>备注

`OpenFile`应在以下情况下使用：

- 应用程序的数据需要作为 FTP 服务器上的文件发送和创建，但该数据不在本地文件中。 打开`OpenFile`文件后，应用程序将使用[CInternetFile：：Write](../../mfc/reference/cinternetfile-class.md#write)将 FTP 文件数据发送到服务器。

- 应用程序必须从服务器检索文件并将其放入应用程序控制的内存中，而不是将其写入磁盘。 应用程序使用[CInternetFile：使用后读取](../../mfc/reference/cinternetfile-class.md#read)`OpenFile`以打开文件。

- 应用程序需要对文件传输进行精细级别的控制。 例如，应用程序可能想要显示进度控件，指示文件传输状态在下载文件时的进度。

`OpenFile`调用后，直到调用`CInternetConnection::Close`， 应用程序只能调用[CInternetFile：：读取](../../mfc/reference/cinternetfile-class.md#read)， [CInternetFile：：写入](../../mfc/reference/cinternetfile-class.md#write)，`CInternetConnection::Close`或[CFtpFile查找：：查找文件](../../mfc/reference/cftpfilefind-class.md#findfile)。 对同一 FTP 会话的其他 FTP 函数的调用将失败，并将错误代码设置为FTP_ETRANSFER_IN_PROGRESS。

*pstrFileName*参数可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `OpenFile`在使用目录名称分隔符之前，将其转换为相应的字符。

覆盖*dwContext*默认值，将上下文标识符设置为您选择的值。 上下文标识符与其`CFtpConnection`[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession：：onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供标识该值的操作的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtp连接：:PutFile

调用此成员函数以在 FTP 服务器上存储文件。

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pstrlocalFile*<br/>
指向从本地系统发送的文件名称的字符串的指针。

*pstrRemoteFile*<br/>
指向在 FTP 服务器上创建的文件名称的字符串的指针。

dwFlags**<br/>
指定文件传输的条件。 可以是[OpenFile](#openfile)中描述的任何FTP_TRANSFER_* 常量。

*dwContext*<br/>
放置文件的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

`PutFile`是一种高级例程，用于处理与在 FTP 服务器上存储文件关联的所有操作。 仅发送数据或需要更密切地控制文件传输的应用程序应使用[OpenFile](#openfile)和[CInternetFile：：write](../../mfc/reference/cinternetfile-class.md#write)。

覆盖`dwContext`默认值，将上下文标识符设置为您选择的值。 上下文标识符与其`CFtpConnection`[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession：：onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供标识该值的操作的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtp 连接：：删除

调用此成员函数从连接的服务器中删除指定的文件。

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>参数

*pstrFile名称*<br/>
指向要删除的文件名的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

*pstrFileName*参数可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 函数`Remove`在使用目录名称分隔符之前将其转换为相应的字符。

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtp 连接：：删除目录

调用此成员函数从连接的服务器中删除指定的目录。

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*普斯特迪尔名称*<br/>
指向包含要删除的目录的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

使用[GetCurrentDirectory](#getcurrentdirectory)确定服务器的当前工作目录。 不要假定远程系统已将您连接到根目录。

*pstrDirName*参数可以是相对于当前目录的部分或完全限定的文件名。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `RemoveDirectory`在使用目录名称分隔符之前，将其转换为相应的字符。

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtp 连接：：重命名

调用此成员函数重命名连接的服务器上的指定文件。

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>参数

*普斯特存在*<br/>
指向要重命名的文件的当前名称的字符串的指针。

*普斯特新*<br/>
指向包含文件新名称的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

*pstr存在*和*pstrNew*参数可以是相对于当前目录的部分限定文件名，也可以是完全限定的。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `Rename`在使用目录名称分隔符之前，将其转换为相应的字符。

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtp 连接：：设置当前目录

调用此成员函数以更改为 FTP 服务器上的不同目录。

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>参数

*普斯特迪尔名称*<br/>
指向包含目录名称的字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

*pstrDirName*参数可以是相对于当前目录的部分或完全限定的文件名。 反斜杠\\（ ） 或正向斜杠 （/） 可用作任一名称的目录分隔符。 `SetCurrentDirectory`在使用目录名称分隔符之前，将其转换为相应的字符。

使用[GetCurrentDirectory](#getcurrentdirectory)确定 FTP 服务器的当前工作目录。 不要假定远程系统已将您连接到根目录。

## <a name="see-also"></a>另请参阅

[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[C 互联网会话类](../../mfc/reference/cinternetsession-class.md)
