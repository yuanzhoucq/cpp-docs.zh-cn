---
title: CInternetSession 类
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: e3d6d319a963fbc24e89bf8c4c0858cd80ec5a9d
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503461"
---
# <a name="cinternetsession-class"></a>CInternetSession 类

创建和初始化一个或多个同时 Internet 会话，并说明与代理服务器的连接（如果需要）。

## <a name="syntax"></a>语法

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|构造 `CInternetSession` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CInternetSession::Close](#close)|当 Internet 会话终止时，请关闭 Internet 连接。|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立状态回调例程。|
|[CInternetSession::GetContext](#getcontext)|当 Internet 会话终止时，请关闭 Internet 连接。|
|[CInternetSession::GetCookie](#getcookie)|返回指定的 URL 和所有父 Url 的 cookie。|
|[CInternetSession::GetCookieLength](#getcookielength)|检索指定的长度存储在缓冲区中的 cookie 的变量。|
|[CInternetSession::GetFtpConnection](#getftpconnection)|打开与服务器的 FTP 会话。 登录用户。|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|将打开 gopher 服务器的应用程序尝试打开的连接。|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|将打开用于尝试打开的连接的应用程序的 HTTP 服务器。|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|启用状态回调时更新操作的状态。|
|[CInternetSession::OpenURL](#openurl)|分析并打开一个 URL。|
|[CInternetSession::SetCookie](#setcookie)|为指定的 URL 设置 cookie。|
|[CInternetSession::SetOption](#setoption)|设置 Internet 会话选项。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|当前 Internet 会话句柄。|

## <a name="remarks"></a>备注

如果你的 Internet 连接必须维护应用程序的持续时间内，则可以创建`CInternetSession`类的成员[CWinApp](../../mfc/reference/cwinapp-class.md)。

一旦已建立 Internet 会话，就可以调用[OpenURL](#openurl)。 `CInternetSession` 然后通过调用全局函数来为您分析 URL [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)。 协议类型，不限`CInternetSession`解释 URL，并为你管理。 它可以处理请求的标识 URL 资源"file://"的本地文件。 `OpenURL` 将返回一个指向[CStdioFile](../../mfc/reference/cstdiofile-class.md)名称将它传递的对象是一个本地文件。

如果您打开上 Internet 服务器使用的 URL `OpenURL`，可以从网站读取信息。 如果你想要在位于服务器上的文件上执行的特定于服务 （如 HTTP、 FTP 或 gopher） 操作，必须建立与该服务器的相应连接。 若要打开特定类型的直接连接到特定服务，请使用以下成员函数之一：

- [GetGopherConnection](#getgopherconnection)以打开与 gopher 服务建立连接。

- [GetHttpConnection](#gethttpconnection)打开对 HTTP 服务的连接。

- [GetFtpConnection](#getftpconnection)以打开与 FTP 服务建立连接。

[SetOption](#setoption)允许您设置的查询选项的会话中，如超时值的重试次数，依次类推。

`CInternetSession` 成员函数[SetCookie](#setcookie)， [GetCookie](#getcookie)，并[GetCookieLength](#getcookielength)提供了用来管理 Win32 cookie 数据库，通过该服务器和脚本维护有关客户端工作站状态信息。

有关基本 Internet 编程任务的详细信息，请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)。 有关使用 MFC WinInet 类的常规信息，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

> [!NOTE]
> `CInternetSession` 将引发[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)为不受支持的服务类型。 目前支持仅以下服务类型：FTP、 HTTP、 gopher 和文件。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>要求

**标头：** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

此成员函数调用时`CInternetSession`创建对象。

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>参数

*pstrAgent*<br/>
指向用于标识应用程序或调用 Internet 函数 （例如，"Microsoft Internet 浏览器"） 的实体的名称的字符串的指针。 如果*pstrAgent*为 NULL （默认值），框架将调用全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname)，它返回以 null 结尾的字符串包含应用程序的名称。 某些协议使用此字符串来标识你的应用程序到服务器。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识返回的操作的状态信息[CInternetSession::OnStatusCallback](#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 将与该上下文 id。 关联的对象以及它执行任何工作

*dwAccessType*<br/>
所需访问权限的类型。 以下是有效的值，其中只有一个可能提供：

- INTERNET_OPEN_TYPE_PRECONFIG 连接使用预配置的注册表中的设置。 此访问类型设置为默认值。 若要通过 TIS 代理进行连接，设置*dwAccessType*为此值; 然后，设置注册表正确。

- INTERNET_OPEN_TYPE_DIRECT 直接连接到 Internet。

- INTERNET_OPEN_TYPE_PROXY 连接通过 CERN 代理。

如何通过不同类型的代理的连接信息，请参阅[典型 FTP 客户端应用程序中的步骤](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxyName*<br/>
首选 CERN 代理服务器的名称如果*dwAccessType*设置为 INTERNET_OPEN_TYPE_PROXY。 默认值为 NULL。

*pstrProxyBypass*<br/>
指向包含一系列可选服务器地址的字符串的指针。 使用代理服务器访问时，可能会跳过这些地址。 如果提供 NULL 值，则将从注册表中读取的旁路列表。 此参数才有意义才*dwAccessType*设置为 INTERNET_OPEN_TYPE_PROXY。

*dwFlags*<br/>
指示各种缓存选项。 默认值设置为 0。 可能值包括：

- INTERNET_FLAG_DONT_CACHE 不缓存数据，在本地或任何网关服务器中。

- 通过持久缓存满足 INTERNET_FLAG_OFFLINE 下载操作。 如果在缓存中不存在项，则返回相应的错误代码。 此标志可以与按位组合**或者**( **&#124;** ) 运算符。

### <a name="remarks"></a>备注

`CInternetSession` 第一个 Internet 函数称为应用程序。 它初始化内部数据结构，并为将来的调用，从应用程序准备好。

如果可以打开无 Internet 连接，`CInternetSession`将引发[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>示例

有关示例，请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="close"></a>  CInternetSession::Close

调用此成员函数，你的应用程序使用完`CInternetSession`对象。

```cpp
virtual void Close();
```

### <a name="example"></a>示例

有关示例，请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

调用此成员函数可启用状态回调。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是启用还是禁用回调。 默认值为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

在处理状态回调时，可以在应用程序的状态栏中提供有关 （如名称解析、 连接到服务器上，依次类推） 操作的进度的状态。 要显示操作状态长期操作期间，尤其是理想。

回调请求的处理过程中出现，因为应用程序应该花尽可能在回调中以防止对网络的数据吞吐量下降，很少的时间。 例如，将出现一个对话框，在回调中可能在被服务器终止请求的此类较长的操作。

只要任何回调处于挂起状态，无法删除状态回调。

若要以异步方式处理的任何操作，您必须创建自己的线程或使用而不使用 MFC WinInet 函数。

## <a name="getcontext"></a>  CInternetSession::GetContext

调用此成员函数可获得的特定应用程序会话上下文值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>返回值

应用程序定义的上下文标识符。

### <a name="remarks"></a>备注

[OnStatusCallback](#onstatuscallback)使用返回的上下文 ID`GetContext`以特定的应用程序状态报告。 例如，当用户激活会返回状态信息的 Internet 请求，状态回调该特定请求上使用报告状态的上下文 ID。 如果用户激活两个单独 Internet 请求都涉及返回状态信息，`OnStatusCallback`上下文标识符用于返回有关其相应的请求的状态。 因此，所有状态回调操作都使用的上下文标识符并且与直到会话结束的会话相关联。

有关异步操作的详细信息，请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)。

## <a name="getcookie"></a>  CInternetSession::GetCookie

此成员函数可实现 Win32 函数的行为[InternetGetCookie](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea)，如 Windows SDK 中所述。

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向包含 URL 的字符串的指针。

*pstrCookieName*<br/>
指向包含要获取为指定的 URL 的 cookie 的名称的字符串的指针。

*pstrCookieData*<br/>
在第一个重载中，指向包含接收的 cookie 数据的缓冲区的地址的字符串的指针。 此值可以为 NULL。 在第二个重载中，对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象接收的 cookie 数据。

*dwBufLen*<br/>
变量指定的大小*pstrCookieData*缓冲区。 如果函数成功，该缓冲区接收复制到的数据量*pstrCookieData*缓冲区。 如果*pstrCookieData*为 NULL，此参数中接收值，指定要复制的所有 cookie 数据所需的缓冲区的大小。

### <a name="return-value"></a>返回值

否则返回如果成功，则为 TRUE 或 FALSE。 如果调用失败，调用 Win32 函数[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。 应用以下的错误值：

- ERROR_NO_MORE_ITEMS 没有任何 cookie 为指定的 URL 和其父项。

- ERROR_INSUFFICIENT_BUFFER 中传递的值*dwBufLen*不足，无法复制的所有 cookie 数据。 中返回的值*dwBufLen*才可获取所有数据缓冲区的大小。

### <a name="remarks"></a>备注

在第二个重载中，MFC 将 cookie 数据检索到所提供`CString`对象。

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

调用此成员函数以获取存储在缓冲区中的 cookie 的长度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向包含 URL 的字符串的指针

*pstrCookieName*<br/>
指向包含的 cookie 的名称的字符串的指针。

### <a name="return-value"></a>返回值

在缓冲区中存储一个 DWORD 值，该值的 cookie 的长度。 如果任何 cookie，则零名称由*pstrCookieName*存在。

### <a name="remarks"></a>备注

此值可供[GetCookie](#getcookie)。

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

调用此成员函数以建立 FTP 连接并获取一个指向`CFtpConnection`对象。

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>参数

*pstrServer*<br/>
指向包含 FTP 服务器名称的字符串的指针。

*pstrUserName*<br/>
指向一个以 null 结尾的字符串，指定要登录的用户的名称。 如果为 NULL，则默认值是匿名的。

*pstrPassword*<br/>
一个指向一个以 null 结尾的字符串，指定要用于登录的密码。 如果这两个*pstrPassword*并*pstrUserName*为 NULL 时，默认匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL （或空字符串），但*pstrUserName*不为 NULL，则使用空密码。 下表描述了四个可能的设置的行为*pstrUserName*并*pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | 发送到 FTP 服务器的用户名 | 发送到 FTP 服务器的密码 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 或""   |   NULL 或""   |         "匿名"         |      用户的电子邮件名称      |
| 非 NULL 字符串 |   NULL 或""   |       *pstrUserName*        |             " "             |
|      NULL       | 非 NULL 字符串 |            错误            |            错误            |
| 非 NULL 字符串 | 非 NULL 字符串 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
标识要在服务器上使用的 TCP/IP 端口号。

*bPassive*<br/>
为此 FTP 会话指定被动还是主动模式。 如果设置为 TRUE，则将设置 Win32 API `dwFlag` INTERNET_FLAG_PASSIVE 到。

### <a name="return-value"></a>返回值

一个指向[CFtpConnection](../../mfc/reference/cftpconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

`GetFtpConnection` 连接到 FTP 服务器，并创建并返回一个指向`CFTPConnection`对象。 它不执行任何服务器上的特定操作。 如果想要读取或写入到文件，例如，必须执行这些操作作为单独的步骤。 请参见类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)并[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)有关搜索文件，打开文件，并读取或写入文件。 请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)中执行常见任务，FTP 连接的步骤。

### <a name="example"></a>示例

有关示例，请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

调用此成员函数建立新的 gopher 连接，获取一个指向`CGopherConnection`对象。

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>参数

*pstrServer*<br/>
指向包含 gopher 服务器名称的字符串的指针。

*pstrUserName*<br/>
指向包含的用户名称的字符串的指针。

*pstrPassword*<br/>
指向包含访问密码的字符串的指针。

*nPort*<br/>
标识要在服务器上使用的 TCP/IP 端口号。

### <a name="return-value"></a>返回值

一个指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

`GetGopherConnection` 连接到 gopher 服务器，并创建并返回一个指向`CGopherConnection`对象。 它不执行任何服务器上的特定操作。 如果想要读取或写入数据，例如，必须执行这些操作作为单独的步骤。 请参见类[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)， [CGopherFile](../../mfc/reference/cgopherfile-class.md)，并[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)有关搜索文件，打开文件，并读取或写入文件。 有关浏览 FTP 站点的信息，请参阅成员函数[OpenURL](#openurl)。 请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)中执行常见 gopher 连接任务的步骤。

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

调用此成员函数以建立 HTTP 连接，并获取一个指向`CHttpConnection`对象。

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>参数

*pstrServer*<br/>
指向包含 HTTP 服务器名称的字符串的指针。

*nPort*<br/>
标识要在服务器上使用的 TCP/IP 端口号。

*pstrUserName*<br/>
指向包含的用户名称的字符串的指针。

*pstrPassword*<br/>
指向包含访问密码的字符串的指针。

*dwflags*<br/>
任意组合`INTERNET_FLAG_*`标志。 请参阅中的表**备注**一部分[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)有关的说明*dwFlags*值。

### <a name="return-value"></a>返回值

一个指向[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

`GetHttpConnection` 连接到 HTTP 服务器，并创建并返回一个指向`CHttpConnection`对象。 它不执行任何服务器上的特定操作。 如果你想要查询的 HTTP 标头，例如，必须执行此操作作为一个单独的步骤。 请参见类[CHttpConnection](../../mfc/reference/chttpconnection-class.md)并[CHttpFile](../../mfc/reference/chttpfile-class.md)可以使用 HTTP 服务器的连接执行的操作有关的信息。 有关浏览 HTTP 站点的信息，请参阅成员函数[OpenURL](#openurl)。 请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)中执行常见的 HTTP 连接任务的步骤。

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

框架可更新的状态，启用状态回调并操作处于挂起状态时调用此成员函数。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>参数

*dwContext*<br/>
由应用程序提供的上下文值。

*dwInternetStatus*<br/>
状态代码指示进行回调。 请参阅**备注**有关可能的值的表。

*lpvStatusInformation*<br/>
指向包含与此回调相关的信息的缓冲区的指针。

*dwStatusInformationLength*<br/>
大小*lpvStatusInformation*。

### <a name="remarks"></a>备注

必须先调用[EnableStatusCallback](#enablestatuscallback)利用状态回调。

*DwInternetStatus*参数指示正在执行的操作，并确定的内容*lpvStatusInformation*将为。 *dwStatusInformationLength*指示中包含的数据的长度*lpvStatusInformation*。 以下状态的值*dwInternetStatus*定义，如下所示：

|值|含义|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|查找名称中包含的 IP 地址*lpvStatusInformation*。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到名称中包含的 IP 地址*lpvStatusInformation*。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|连接到套接字地址 ([SOCKADDR](/windows/desktop/winsock/sockaddr-2)) 由指向*lpvStatusInformation*。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|已成功连接到套接字地址 (SOCKADDR) 指向*lpvStatusInformation*。|
|INTERNET_STATUS_SENDING_REQUEST|向服务器发送信息请求。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_ REQUEST_SENT|已成功发送到服务器的信息请求。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_RECEIVING_RESPONSE|正在等待服务器响应的请求。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功从服务器收到的响应。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_CLOSING_CONNECTION|正在关闭服务器的连接。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_CONNECTION_CLOSED|已成功关闭了连接到服务器。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_HANDLE_CREATED|使用 Win32 API 函数[InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta)以指示它已创建新的句柄。 这可让应用程序调用 Win32 函数[InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle)从另一个线程如果连接所需时间太长。 请参阅 Windows SDKfor 有关这些函数的详细信息。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功终止此句柄值。|

重写此成员函数以执行状态回调例程之前需要执行一些操作。

> [!NOTE]
> 状态回调需要线程状态保护。 如果在共享库中使用 MFC，重写的开头添加以下行：

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

有关异步操作的详细信息，请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)。

## <a name="openurl"></a>  CInternetSession::OpenURL

调用此成员函数将指定的请求发送到 HTTP 服务器，并允许客户端可以指定其他 RFC822 MIME 或要连同请求一起发送 HTTP 标头。

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>参数

*pstrURL*<br/>
一个指向的 URL 以开始读取的名称。 仅 Url 开头文件:，ftp:，gopher:，或 http： 支持。 如果断言*pstrURL*为 NULL。

*dwContext*<br/>
使用回调中返回的句柄传递的应用程序定义的值。

*dwFlags*<br/>
描述如何处理此连接的标志。 请参阅**备注**有关有效的标志的详细信息。 是有效的标志：

- INTERNET_FLAG_TRANSFER_ASCII 默认值。 将文件传输为 ASCII 文本。

- INTERNET_FLAG_TRANSFER_BINARY 传输该文件为二进制文件。

- 即使本地缓存 INTERNET_FLAG_RELOAD 从网络中获取数据。

- INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。

- 适用于 HTTP 请求仅 INTERNET_FLAG_SECURE 此标志。 它会请求使用安全套接字层或百分比在网络上的安全事务

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 如果可能，请重复使用的生成的新请求服务器的现有连接`OpenUrl`而不是创建新的会话的每个连接请求。

- INTERNET_FLAG_PASSIVE 用于 FTP 站点。 使用被动 FTP 语义。 用于[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)的`OpenURL`。

*pstrHeaders*<br/>
指向包含要发送到 HTTP 服务器的标头的字符串的指针。

*dwHeadersLength*<br/>
长度 （以字符为单位的其他标头）。 如果这是-1l 并*pstrHeaders*为非 NULL，则*pstrHeaders*假设为零终止，并且长度进行计算。

### <a name="return-value"></a>返回值

返回 FTP、 GOPHER、 HTTP 和文件类型 Internet 服务的文件句柄。 如果分析成功，则返回 NULL。

指针的`OpenURL`取决于返回*pstrURL*的服务的类型。 下表说明了可能的指针`OpenURL`可以返回。

|URL 类型|返回|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>备注

将参数*dwFlags*必须包括 INTERNET_FLAG_TRANSFER_ASCII 或 INTERNET_FLAG_TRANSFER_BINARY，但不可同时使用两者。 可以使用按位组合剩余标志**或者**运算符 ( **&#124;** )。

`OpenURL`其包装 Win32 函数`InternetOpenURL`，允许仅下载、 检索和从 Internet 服务器读取的数据。 `OpenURL` 允许在远程位置中的没有文件处理，因此不需要它[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)对象。

若要使用特定于连接的 (即，特定于协议的) 函数，如对文件进行写入，您必须打开的会话，然后打开特定类型的连接，然后使用该连接所需的模式中打开文件。 请参阅`CInternetConnection`有关特定于连接的函数的详细信息。

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

此运算符用于获取当前的 Internet 会话的 Windows 句柄。

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

为指定的 URL 设置 cookie。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向一个以 null 结尾的字符串，指定应为其设置 cookie 的 URL 的指针。

*pstrCookieName*<br/>
指向包含的 cookie 的名称的字符串的指针。

*pstrCookieData*<br/>
指向包含要将 URL 与相关联的实际字符串数据的字符串的指针。

### <a name="return-value"></a>返回值

否则返回如果成功，则为 TRUE 或 FALSE。 若要获取特定错误代码，调用 `GetLastError.`

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea)，如 Windows SDK 中所述。

## <a name="setoption"></a>  CInternetSession::SetOption

调用此成员函数以设置 Internet 会话选项。

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>参数

*dwOption*<br/>
若要设置 Internet 选项。 请参阅[选项标志](/windows/desktop/WinInet/option-flags)Windows SDKfor 的可能的选项列表中。

*lpBuffer*<br/>
包含的选项设置的缓冲区。

*dwBufferLength*<br/>
长度*lpBuffer*或的大小*dwValue*。

*dwValue*<br/>
一个包含选项设置的 dword 值。

*dwFlags*<br/>
指示各种缓存选项。 默认值设置为 0。 可能值包括：

- INTERNET_FLAG_DONT_CACHE 不缓存数据，在本地或任何网关服务器中。

- 通过持久缓存满足 INTERNET_FLAG_OFFLINE 下载操作。 如果在缓存中不存在项，则返回相应的错误代码。 此标志可以与按位组合**或者**( **&#124;** ) 运算符。

### <a name="return-value"></a>返回值

如果操作成功，则返回值为 TRUE。 如果遇到错误，则返回值为 FALSE。 如果调用失败，Win32 函数[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)可能调用以确定错误的原因。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 类](../../mfc/reference/cgopherconnection-class.md)
