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
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505846"
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
|[CInternetSession::Close](#close)|在 Internet 会话终止时关闭 Internet 连接。|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立状态回调例程。|
|[CInternetSession::GetContext](#getcontext)|在 Internet 会话终止时关闭 Internet 连接。|
|[CInternetSession::GetCookie](#getcookie)|为指定的 URL 及其所有父 Url 返回 cookie。|
|[CInternetSession::GetCookieLength](#getcookielength)|检索指定存储在缓冲区中的 cookie 长度的变量。|
|[CInternetSession::GetFtpConnection](#getftpconnection)|打开与服务器的 FTP 会话。 用户的日志。|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|为尝试打开连接的应用程序打开 gopher 服务器。|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|为尝试打开连接的应用程序打开 HTTP 服务器。|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|当启用状态回调时更新操作的状态。|
|[CInternetSession::OpenURL](#openurl)|分析并打开 URL。|
|[CInternetSession::SetCookie](#setcookie)|为指定的 URL 设置 cookie。|
|[CInternetSession::SetOption](#setoption)|设置 Internet 会话的选项。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|当前 Internet 会话的句柄。|

## <a name="remarks"></a>备注

如果必须在应用程序持续时间内维护 Internet 连接, 则可以创建`CInternetSession`类[CWinApp](../../mfc/reference/cwinapp-class.md)的成员。

建立 Internet 会话后, 可以调用[OpenURL](#openurl)。 `CInternetSession`然后通过调用全局函数[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)分析 URL。 无论其协议类型如何, `CInternetSession`都会解释 URL 并对其进行管理。 它可以处理用 URL 资源 "file://" 标识的本地文件的请求。 `OpenURL`如果传递的名称是本地文件, 则将返回指向[CStdioFile](../../mfc/reference/cstdiofile-class.md)对象的指针。

如果使用`OpenURL`打开 Internet 服务器上的 URL, 则可从网站读取信息。 如果要对服务器上的文件执行特定于服务的操作 (例如 HTTP、FTP 或 gopher), 则必须与该服务器建立适当的连接。 若要将特定类型的连接直接打开到特定服务, 请使用下列成员函数之一:

- [GetGopherConnection](#getgopherconnection)打开与 gopher 服务的连接。

- [GetHttpConnection](#gethttpconnection)打开到 HTTP 服务的连接。

- [GetFtpConnection](#getftpconnection)打开与 FTP 服务的连接。

[SetOption](#setoption)允许您设置会话的查询选项, 例如超时值、重试次数等。

`CInternetSession`成员函数[system.windows.application.setcookie](#setcookie)、 [system.windows.application.getcookie](#getcookie)和[GetCookieLength](#getcookielength)提供了管理 Win32 cookie 数据库的方法, 服务器和脚本通过该数据库维护有关客户端工作站的状态信息。

有关基本的 internet 编程任务的详细信息, 请参阅[文章 internet 第一步:WinInet](../../mfc/wininet-basics.md)。 有关使用 MFC WinInet 类的常规信息, 请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

> [!NOTE]
> `CInternetSession`将对不受支持的服务类型引发[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) 。 目前仅支持以下服务类型:FTP、HTTP、gopher 和 file。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>要求

**标头:** afxinet。h

## <a name="cinternetsession"></a>CInternetSession:: CInternetSession

当创建`CInternetSession`对象时, 将调用此成员函数。

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
指向字符串的指针, 该字符串标识调用 Internet 函数的应用程序或实体的名称 (例如, "Microsoft Internet 浏览器")。 如果*pstrAgent*为 NULL (默认值), 则框架将调用全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname), 这将返回一个以 NULL 结尾的字符串, 该字符串包含应用程序的名称。 某些协议使用此字符串来向服务器标识您的应用程序。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识由[CInternetSession:: OnStatusCallback](#onstatuscallback)返回的操作的状态信息。 默认值设置为 1;但是, 您可以显式分配操作的特定上下文 ID。 对象及其执行的所有工作都将与该上下文 ID 相关联。

*dwAccessType*<br/>
所需的访问类型。 下面是有效值, 其中可能提供了以下值之一:

- INTERNET_OPEN_TYPE_PRECONFIG 使用注册表中的预配置设置进行连接。 此访问类型设置为默认值。 若要通过 TIS 代理进行连接, 请将*dwAccessType*设置为此值;然后, 相应地设置注册表。

- INTERNET_OPEN_TYPE_DIRECT 直接连接到 Internet。

- INTERNET_OPEN_TYPE_PROXY 通过 CERN 代理进行连接。

有关使用不同类型的代理进行连接的信息, 请参阅[典型 FTP 客户端应用程序中的步骤](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxyName*<br/>
如果*dwAccessType*设置为 INTERNET_OPEN_TYPE_PROXY, 则为首选的 CERN 代理的名称。 默认值为 NULL。

*pstrProxyBypass*<br/>
指向包含可选服务器地址列表的字符串的指针。 使用代理访问时, 可能会绕过这些地址。 如果提供了 NULL 值, 则将从注册表中读取绕过列表。 仅当*dwAccessType*设置为 INTERNET_OPEN_TYPE_PROXY 时, 此参数才有意义。

*dwFlags*<br/>
指示各种缓存选项。 默认值设置为0。 可能的值包括:

- INTERNET_FLAG_DONT_CACHE 不会在本地或任何网关服务器中缓存数据。

- INTERNET_FLAG_OFFLINE 下载操作仅通过永久性缓存得到满足。 如果缓存中不存在该项, 则返回相应的错误代码。 此标志可以与按位**or** ( **&#124;** ) 运算符组合在一起。

### <a name="remarks"></a>备注

`CInternetSession`是应用程序调用的第一个 Internet 函数。 它初始化内部数据结构, 并为将来的应用程序调用做好准备。

如果无法打开 Internet 连接, `CInternetSession`则会引发[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>示例

请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的示例。

## <a name="close"></a>  CInternetSession::Close

当应用程序使用完对象后, `CInternetSession`调用此成员函数。

```cpp
virtual void Close();
```

### <a name="example"></a>示例

请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的示例。

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

调用此成员函数以启用状态回调。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是启用还是禁用回叫。 默认值为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

处理状态回调时, 可以在应用程序的状态栏中提供有关操作进度 (例如, 解析名称、连接到服务器等) 的状态。 在长期操作期间, 显示操作状态特别合适。

由于回调发生在请求的处理过程中, 因此应用程序应尽可能少地在回调中花费很长时间, 以防网络的数据吞吐量下降。 例如, 在回调中放置一个对话框可能会导致服务器终止请求的时间较长的操作。

只要有挂起的回调, 就不能删除状态回调。

若要以异步方式处理任何操作, 必须创建自己的线程或使用不带 MFC 的 WinInet 函数。

## <a name="getcontext"></a>CInternetSession:: GetContext

调用此成员函数可获取特定应用程序会话的上下文值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>返回值

应用程序定义的上下文标识符。

### <a name="remarks"></a>备注

[OnStatusCallback](#onstatuscallback)使用返回`GetContext`的上下文 ID 报告特定应用程序的状态。 例如, 当用户激活涉及返回状态信息的 Internet 请求时, 状态回调将使用上下文 ID 报告该特定请求的状态。 如果用户激活两个分别涉及返回状态信息的不同 Internet 请求, `OnStatusCallback`将使用上下文标识符返回与相应请求相关的状态。 因此, 上下文标识符用于所有状态回调操作, 并且它与会话相关联, 直到会话结束为止。

有关异步操作的详细信息, 请参阅文章[Internet 第一步:WinInet](../../mfc/wininet-basics.md)。

## <a name="getcookie"></a>  CInternetSession::GetCookie

此成员函数实现 Win32 函数[InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)的行为, 如 Windows SDK 中所述。

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
指向字符串的指针, 该字符串包含要为指定的 URL 获取的 cookie 的名称。

*pstrCookieData*<br/>
在第一个重载中, 是指向字符串的指针, 该字符串包含接收 cookie 数据的缓冲区的地址。 此值可以为 NULL。 在第二个重载中, 是对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用, 用于接收 cookie 数据。

*dwBufLen*<br/>
指定*pstrCookieData*缓冲区大小的变量。 如果该函数成功, 则缓冲区将接收复制到*pstrCookieData*缓冲区的数据量。 如果*pstrCookieData*为 NULL, 则此参数接收一个值, 该值指定复制所有 cookie 数据所需的缓冲区大小。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE; 否则返回 FALSE。 如果调用失败, 请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。 以下错误值适用:

- ERROR_NO_MORE_ITEMS 指定的 URL 及其所有父项没有 cookie。

- ERROR_INSUFFICIENT_BUFFER 在*dwBufLen*中传递的值不足以复制所有 cookie 数据。 *DwBufLen*中返回的值是获取所有数据所需的缓冲区大小。

### <a name="remarks"></a>备注

在第二个重载中, MFC 将 cookie 数据检索到`CString`提供的对象。

## <a name="getcookielength"></a>CInternetSession:: GetCookieLength

调用此成员函数以获取存储在缓冲区中的 cookie 的长度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向包含 URL 的字符串的指针。

*pstrCookieName*<br/>
指向包含 cookie 名称的字符串的指针。

### <a name="return-value"></a>返回值

指示存储在缓冲区中的 cookie 长度的 DWORD 值。 如果*pstrCookieName*不存在具有指定名称的 cookie, 则为零。

### <a name="remarks"></a>备注

此值由[system.windows.application.getcookie](#getcookie)使用。

## <a name="getftpconnection"></a>CInternetSession:: GetFtpConnection

调用此成员函数以建立 FTP 连接并获取指向`CFtpConnection`对象的指针。

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
指向以 null 结尾的字符串的指针, 该字符串指定要登录的用户的名称。 如果为 NULL, 则默认值为 anonymous。

*pstrPassword*<br/>
指向以 null 结尾的字符串的指针, 该字符串指定用于登录的密码。 如果*pstrPassword*和*PSTRUSERNAME*都为 NULL, 则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 null (或空字符串), 但*PSTRUSERNAME*不为 null, 则使用空密码。 下表描述了*pstrUserName*和*pstrPassword*的四个可能设置的行为:

| *pstrUserName*  | *pstrPassword*  | 发送到 FTP 服务器的用户名 | 发送到 FTP 服务器的密码 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 或 ""   |   NULL 或 ""   |         匿名         |      用户的电子邮件名称      |
| 非空字符串 |   NULL 或 ""   |       *pstrUserName*        |             " "             |
|      NULL       | 非空字符串 |            错误            |            错误            |
| 非空字符串 | 非空字符串 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
一个数字, 用于标识服务器上要使用的 TCP/IP 端口。

*bPassive*<br/>
为此 FTP 会话指定被动或主动模式。 如果设置为 TRUE, 则将 Win32 API `dwFlag`设置为 INTERNET_FLAG_PASSIVE。

### <a name="return-value"></a>返回值

指向[CFtpConnection](../../mfc/reference/cftpconnection-class.md)对象的指针。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetFtpConnection`连接到 FTP 服务器, 并创建并返回一个指向`CFTPConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如, 如果你想要读取或写入文件, 则必须以单独的步骤执行这些操作。 有关搜索文件、打开文件和读取或写入文件的信息, 请参阅类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 。 请参阅文章[带有 WinInet 的 Internet 编程](../../mfc/win32-internet-extensions-wininet.md), 了解执行常见 FTP 连接任务中的步骤。

### <a name="example"></a>示例

请参阅[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的示例。

## <a name="getgopherconnection"></a>CInternetSession:: GetGopherConnection

调用此成员函数以建立新的 gopher 连接并获取指向`CGopherConnection`对象的指针。

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
指向包含用户名的字符串的指针。

*pstrPassword*<br/>
指向包含访问密码的字符串的指针。

*nPort*<br/>
一个数字, 用于标识服务器上要使用的 TCP/IP 端口。

### <a name="return-value"></a>返回值

指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象的指针。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetGopherConnection`连接到 gopher 服务器, 并创建并返回指向`CGopherConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如, 如果你想要读取或写入数据, 则必须以单独的步骤执行这些操作。 有关搜索文件、打开文件和读取或写入文件的信息, 请参阅[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)、 [CGopherFile](../../mfc/reference/cgopherfile-class.md)和[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)类。 有关浏览 FTP 站点的信息, 请参阅成员函数[OpenURL](#openurl)。 请参阅文章[带有 WinInet 的 Internet 编程](../../mfc/win32-internet-extensions-wininet.md), 了解执行常见 gopher 连接任务中的步骤。

## <a name="gethttpconnection"></a>CInternetSession:: GetHttpConnection

调用此成员函数以建立 HTTP 连接并获取指向`CHttpConnection`对象的指针。

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
一个数字, 用于标识服务器上要使用的 TCP/IP 端口。

*pstrUserName*<br/>
指向包含用户名的字符串的指针。

*pstrPassword*<br/>
指向包含访问密码的字符串的指针。

*dwflags*<br/>
`INTERNET_FLAG_*`标志的任意组合。 有关*dwFlags*值的说明, 请参阅[CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)的 "**备注**" 部分中的表。

### <a name="return-value"></a>返回值

指向[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象的指针。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetHttpConnection`连接到 HTTP 服务器, 并创建并返回指向`CHttpConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如, 如果想要查询 HTTP 标头, 则必须以单独的步骤执行此操作。 有关可以通过使用 HTTP 服务器连接执行的操作的信息, 请参阅[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md)类。 有关浏览 HTTP 站点的信息, 请参阅成员函数[OpenURL](#openurl)。 请参阅文章[带有 WinInet 的 Internet 编程](../../mfc/win32-internet-extensions-wininet.md), 了解执行常见 HTTP 连接任务中的步骤。

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

当启用状态回调并且操作处于挂起状态时, 框架将调用此成员函数以更新状态。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>参数

*dwContext*<br/>
应用程序提供的上下文值。

*dwInternetStatus*<br/>
指示何时进行回调的状态代码。 有关可能值的表, 请参阅 "**备注**"。

*lpvStatusInformation*<br/>
指向包含与此回调相关的信息的缓冲区的指针。

*dwStatusInformationLength*<br/>
*LpvStatusInformation*的大小。

### <a name="remarks"></a>备注

必须先调用[EnableStatusCallback](#enablestatuscallback) , 才能利用状态回调。

*DwInternetStatus*参数指示要执行的操作, 并确定*lpvStatusInformation*的内容。 *dwStatusInformationLength*指示*lpvStatusInformation*中包含的数据的长度。 *DwInternetStatus*的以下状态值定义如下:

|值|含义|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|查找*lpvStatusInformation*中包含的名称的 IP 地址。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到*lpvStatusInformation*中包含的名称的 IP 地址。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|连接到*lpvStatusInformation*指向的套接字地址 ([SOCKADDR](/windows/win32/winsock/sockaddr-2))。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|已成功连接到*lpvStatusInformation*指向的套接字地址 (SOCKADDR)。|
|INTERNET_STATUS_SENDING_REQUEST|将信息请求发送到服务器。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_ REQUEST_SENT|已成功将信息请求发送到服务器。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_RECEIVING_RESPONSE|正在等待服务器响应请求。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功从服务器接收响应。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_CLOSING_CONNECTION|正在关闭与服务器的连接。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_CONNECTION_CLOSED|已成功关闭与服务器的连接。 *LpvStatusInformation*参数为 NULL。|
|INTERNET_STATUS_HANDLE_CREATED|由 Win32 API 函数[InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw)用来指示它已创建新句柄。 这样, 如果连接时间太长, 应用程序就可以从其他线程调用 Win32 函数[InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) 。 有关这些功能的详细信息, 请参阅 Windows SDKfor。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功终止此句柄值。|

在执行状态回调例程之前, 重写此成员函数以要求执行一些操作。

> [!NOTE]
> 状态回调需要线程状态保护。 如果使用的是共享库中的 MFC, 请将以下行添加到重写的开头:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

有关异步操作的详细信息, 请参阅文章[Internet 第一步:WinInet](../../mfc/wininet-basics.md)。

## <a name="openurl"></a>CInternetSession:: OpenURL

调用此成员函数以将指定的请求发送到 HTTP 服务器, 并允许客户端指定要与请求一起发送的其他 RFC822、MIME 或 HTTP 标头。

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
一个指针, 指向要开始读取的 URL 的名称。 仅支持以 file:、ftp:、gopher: 或 http: 开头的 Url。 如果*pstrURL*为 NULL, 则断言。

*dwContext*<br/>
在回调中通过返回的句柄传递的应用程序定义值。

*dwFlags*<br/>
描述如何处理此连接的标志。 有关有效标志的详细信息, 请参阅 "**备注**"。 有效标志为:

- INTERNET_FLAG_TRANSFER_ASCII 默认值。 将文件作为 ASCII 文本传输。

- INTERNET_FLAG_TRANSFER_BINARY 将文件作为二进制文件传输。

- INTERNET_FLAG_RELOAD 从线路获取数据, 即使该数据在本地缓存也是如此。

- INTERNET_FLAG_DONT_CACHE 不会在本地或任何网关上缓存数据。

- INTERNET_FLAG_SECURE 此标志仅适用于 HTTP 请求。 它通过安全套接字层或 PCT 请求线路上的安全事务。

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 如果可能, 为生成的`OpenUrl`新请求重用服务器的现有连接, 而不是为每个连接请求创建新的会话。

- 用于 FTP 站点的 INTERNET_FLAG_PASSIVE。 使用被动 FTP 语义。 与`OpenURL`的[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)一起使用。

*pstrHeaders*<br/>
指向字符串的指针, 该字符串包含要发送到 HTTP 服务器的标头。

*dwHeadersLength*<br/>
附加标头的长度, 以字符为字符。 如果此值为-1L 且*pstrHeaders*为非 NULL, 则假定*pstrHeaders*为零终止, 并计算长度。

### <a name="return-value"></a>返回值

返回仅适用于 FTP、GOPHER、HTTP 和文件类型 Internet 服务的文件句柄。 如果分析失败, 则返回 NULL。

`OpenURL`返回的指针依赖于*pstrURL*的服务类型。 下表说明了可能的指针`OpenURL`可以返回。

|URL 类型|返回|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>备注

参数*dwFlags*必须包括 INTERNET_FLAG_TRANSFER_ASCII 或 INTERNET_FLAG_TRANSFER_BINARY, 但不能同时包含两者。 其余标志可以与按位 "**或**" 运算符 ( **&#124;** ) 组合。

`OpenURL`, 它包装 Win32 函数`InternetOpenURL`, 只允许从 Internet 服务器下载、检索和读取数据。 `OpenURL`不允许在远程位置进行文件操作, 因此它不需要[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)对象。

若要使用特定于连接的 (即特定于协议的) 功能 (如写入文件), 必须打开一个会话, 然后打开特定类型的连接, 然后使用该连接以所需的模式打开文件。 有关`CInternetConnection`特定于连接的函数的详细信息, 请参阅。

## <a name="operator_hinternet"></a>CInternetSession:: operator HINTERNET

使用此运算符可获取当前 Internet 会话的 Windows 句柄。

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
指向以 null 结尾的字符串的指针, 该字符串指定应为其设置 cookie 的 URL。

*pstrCookieName*<br/>
指向包含 cookie 名称的字符串的指针。

*pstrCookieData*<br/>
指向字符串的指针, 该字符串包含与 URL 关联的实际字符串数据。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE; 否则返回 FALSE。 若要获取特定的错误代码, 请调用`GetLastError.`

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)的行为, 如 Windows SDK 中所述。

## <a name="setoption"></a>  CInternetSession::SetOption

调用此成员函数可设置 Internet 会话的选项。

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
要设置的 Internet 选项。 有关可能选项的列表, 请参阅 Windows SDKfor 中的[选项标志](/windows/win32/WinInet/option-flags)。

*lpBuffer*<br/>
包含选项设置的缓冲区。

*dwBufferLength*<br/>
*LpBuffer*的长度或*dwValue*的大小。

*dwValue*<br/>
包含选项设置的 DWORD。

*dwFlags*<br/>
指示各种缓存选项。 默认值设置为0。 可能的值包括:

- INTERNET_FLAG_DONT_CACHE 不会在本地或任何网关服务器中缓存数据。

- INTERNET_FLAG_OFFLINE 下载操作仅通过永久性缓存得到满足。 如果缓存中不存在该项, 则返回相应的错误代码。 此标志可以与按位**or** ( **&#124;** ) 运算符组合在一起。

### <a name="return-value"></a>返回值

如果操作成功, 则返回值 TRUE。 如果出现错误, 则返回值 FALSE。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 类](../../mfc/reference/cgopherconnection-class.md)
