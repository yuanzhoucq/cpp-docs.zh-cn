---
title: C 互联网会话类
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
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372380"
---
# <a name="cinternetsession-class"></a>C 互联网会话类

创建和初始化一个或多个同时 Internet 会话，并说明与代理服务器的连接（如果需要）。

## <a name="syntax"></a>语法

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 互联网会话：：C 互联网会话](#cinternetsession)|构造 `CInternetSession` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 互联网会话：关闭](#close)|终止 Internet 会话时关闭 Internet 连接。|
|[CInternet 会话：：启用状态回调](#enablestatuscallback)|建立状态回调例程。|
|[C 互联网会话：获取上下文](#getcontext)|终止 Internet 会话时关闭 Internet 连接。|
|[C 互联网会话：：获取 Cookie](#getcookie)|返回指定 URL 及其所有父 URL 的 Cookie。|
|[C 互联网会话：：获取 Cookie 长度](#getcookielength)|检索指定存储在缓冲区中的 Cookie 长度的变量。|
|[C 互联网会话：：获取Ftp连接](#getftpconnection)|打开与服务器的 FTP 会话。 在用户上登录。|
|[C 互联网会话：：获取 Gopher 连接](#getgopherconnection)|为尝试打开连接的应用程序打开 gopher 服务器。|
|[C 互联网会话：：获取Http连接](#gethttpconnection)|为尝试打开连接的应用程序打开 HTTP 服务器。|
|[CInternet 会话：：打开状态回拨](#onstatuscallback)|启用状态回调时更新操作的状态。|
|[C 互联网会话：：打开 URL](#openurl)|分析并打开 URL。|
|[C 互联网会话：：SetCookie](#setcookie)|为指定的 URL 设置 Cookie。|
|[C 互联网会话：：设置选项](#setoption)|设置 Internet 会话的选项。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C 互联网会话：：操作员 HINTERNET](#operator_hinternet)|当前 Internet 会话的句柄。|

## <a name="remarks"></a>备注

如果必须在应用程序的持续时间内维护 Internet 连接，则可以创建类`CInternetSession`[CWinApp](../../mfc/reference/cwinapp-class.md)的成员。

建立 Internet 会话后，可以调用[OpenURL](#openurl)。 `CInternetSession`然后通过调用全局函数[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)来分析 URL。 无论协议类型如何，`CInternetSession`都解释 URL 并为您管理它。 它可以处理使用 URL 资源"file://"标识的本地文件的请求。 `OpenURL`如果传递的名称是本地文件，则返回指向[CStdioFile](../../mfc/reference/cstdiofile-class.md)对象的指针。

如果使用 在 Internet 服务器上打开`OpenURL`URL，则可以从站点读取信息。 如果要对服务器上的文件执行特定于服务的操作（例如 HTTP、FTP 或 gopher）操作，则必须与该服务器建立适当的连接。 要直接打开与特定服务的特定类型的连接，请使用以下成员函数之一：

- [获取 Gopher 连接](#getgopherconnection)以打开到 gopher 服务的连接。

- [获取 HttpConnection](#gethttpconnection)以打开与 HTTP 服务的连接。

- [获取 Ftp 连接](#getftpconnection)以打开与 FTP 服务的连接。

[SetOption](#setoption)允许您设置会话的查询选项，如超时值、重试次数等。

`CInternetSession`成员函数[SetCookie、GetCookie](#setcookie)和[GetCookieLength](#getcookielength)提供了管理 Win32 Cookie 数据库的方法，通过该数据库，服务器和脚本通过该数据库维护有关客户端工作站的状态信息。 [GetCookie](#getcookie)

有关基本 Internet 编程任务的详细信息，请参阅文章["互联网第一步：WinInet](../../mfc/wininet-basics.md)"。 有关使用 MFC WinInet 类的一般信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

> [!NOTE]
> `CInternetSession`将为不支持的服务类型引发[AfxThrow 不支持的例外。](exception-processing.md#afxthrownotsupportedexception) 目前仅支持以下服务类型：FTP、HTTP、gopher 和文件。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>C 互联网会话：：C 互联网会话

创建`CInternetSession`对象时将调用此成员函数。

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

*普斯特代理*<br/>
指向标识调用 Internet 函数的应用程序或实体名称的字符串的指针（例如，"微软互联网浏览器"）。 如果*pstrAgent*为 NULL（默认值），则框架将调用全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname)，该函数返回包含应用程序名称的 null 端接字符串。 某些协议使用此字符串向服务器标识应用程序。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识 CInternetSession 返回的操作的状态信息[：：onStatusCallback](#onstatuscallback)。 默认值设置为 1;将默认值设置为 1但是，您可以显式为操作分配特定的上下文 ID。 对象及其执行的任何工作都将与该上下文 ID 相关联。

*dwAccess类型*<br/>
所需的访问类型。 以下是有效的值，其中一个值可能提供：

- INTERNET_OPEN_TYPE_PRECONFIG 使用注册表中的预配置设置连接。 此访问类型设置为默认值。 要通过 TIS 代理进行连接，请将*dwAccessType*设置为此值;但是，通过 TIS 代理进行连接。然后，您可以适当地设置注册表。

- INTERNET_OPEN_TYPE_DIRECT直接连接到互联网。

- INTERNET_OPEN_TYPE_PROXY通过欧洲核子研究中心代理连接。

有关与不同类型的代理连接的信息，请参阅[典型 FTP 客户端应用程序中的步骤](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxy名称*<br/>
如果*dwAccessType*设置为INTERNET_OPEN_TYPE_PROXY，则首选 CERN 代理的名称。 默认值为 NULL。

*pstrProxy旁路*<br/>
指向包含可选服务器地址列表的字符串的指针。 使用代理访问时，可能会绕过这些地址。 如果提供了 NULL 值，则从注册表中读取绕过列表。 仅当*dwAccessType*设置为INTERNET_OPEN_TYPE_PROXY时，此参数才有意义。

dwFlags**<br/>
指示各种缓存选项。 默认值设置为 0。 可能的值包括：

- INTERNET_FLAG_DONT_CACHE不要在本地或任何网关服务器中缓存数据。

- INTERNET_FLAG_OFFLINE仅通过持久缓存满足下载操作。 如果缓存中不存在该项目，则返回相应的错误代码。 此标志可与位**或**（ **&#124;**） 运算符组合。

### <a name="remarks"></a>备注

`CInternetSession`是应用程序调用的第一个 Internet 函数。 它初始化内部数据结构，并为将来从应用程序调用做好准备。

如果没有互联网连接可以打开，`CInternetSession`抛出一个[AfxThrow互联网例外](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>示例

请参阅[CFtpFileFind 的示例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessionclose"></a><a name="close"></a>C 互联网会话：关闭

当应用程序完成使用对象后，`CInternetSession`调用此成员函数。

```cpp
virtual void Close();
```

### <a name="example"></a>示例

请参阅[CFtpFileFind 的示例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternet 会话：：启用状态回调

调用此成员函数以启用状态回调。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定回调是启用还是禁用。 默认值为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

处理状态回调时，可以在应用程序的状态栏中提供有关操作进度（如解析名称、连接到服务器等）的状态。 在长期操作期间，显示操作状态特别可取。

由于回调发生在请求处理期间，因此应用程序应在回调中花费尽可能少的时间，以防止对网络的数据吞吐量下降。 例如，在回调中放置对话框可能是一个冗长的操作，以至于服务器终止了请求。

只要任何回调是挂起的，则无法删除状态回调。

要异步处理任何操作，必须创建自己的线程或使用没有 MFC 的 WinInet 函数。

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>C 互联网会话：获取上下文

调用此成员函数获取特定应用程序会话的上下文值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>返回值

应用程序定义的上下文标识符。

### <a name="remarks"></a>备注

[OnStatusCallback](#onstatuscallback)使用 返回`GetContext`的上下文 ID 来报告特定应用程序的状态。 例如，当用户激活涉及返回状态信息的 Internet 请求时，状态回调将使用上下文 ID 报告该特定请求的状态。 如果用户激活两个涉及返回状态信息的单独 Internet 请求，`OnStatusCallback`则使用上下文标识符返回其相应请求的状态。 因此，上下文标识符用于所有状态回调操作，并且它与会话关联，直到会话结束。

有关异步操作的详细信息，请参阅文章["Internet 第一步：WinInet](../../mfc/wininet-basics.md)"。

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>C 互联网会话：：获取 Cookie

此成员函数实现 Win32 函数[InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)的行为，如 Windows SDK 中所述。

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

*普斯特库奇名称*<br/>
指向包含 Cookie 名称的字符串的指针，用于获取指定 URL 的名称。

*普斯特库奇数据*<br/>
在第一个重载中，指向包含接收 Cookie 数据的缓冲区地址的字符串的指针。 此值可以是 NULL。 在第二个重载中，对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用以接收 Cookie 数据。

*德布夫伦*<br/>
指定*pstrCookieData*缓冲区大小的变量。 如果函数成功，缓冲区将收到复制到*pstrCookieData*缓冲区的数据量。 如果*pstrCookieData*为 NULL，则此参数将接收指定复制所有 Cookie 数据所需的缓冲区大小的值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。 如果呼叫失败，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。 应用以下错误值：

- ERROR_NO_MORE_ITEMS指定 URL 及其所有父 URL 没有 Cookie。

- ERROR_INSUFFICIENT_BUFFER *dwBufLen*中传递的值不足以复制所有 Cookie 数据。 *在 dwBufLen*中返回的值是获取所有数据所需的缓冲区的大小。

### <a name="remarks"></a>备注

在第二个重载中，MFC 将 Cookie 数据`CString`检索到提供的对象中。

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>C 互联网会话：：获取 Cookie 长度

调用此成员函数获取存储在缓冲区中的 Cookie 的长度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向包含 URL 的字符串的指针

*普斯特库奇名称*<br/>
指向包含 Cookie 名称的字符串的指针。

### <a name="return-value"></a>返回值

DWORD 值，指示存储在缓冲区中的 Cookie 的长度。 如果存在带有*pstrCookieName*指示的名称的 Cookie，则为零。

### <a name="remarks"></a>备注

此值由[GetCookie](#getcookie)使用。

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>C 互联网会话：：获取Ftp连接

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

*pstrUser 名称*<br/>
指向 null 终止字符串的指针，该字符串指定要登录的用户的名称。 如果为 NULL，则默认值为匿名。

*pstr密码*<br/>
指向 null 终止字符串的指针，用于指定用于登录的密码。 如果*pstrPassword*和*pstrUserName*均为 NULL，则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL（或空字符串），但*pstrUserName*不是 NULL，则使用空白密码。 下表描述了*pstrUserName*和*pstrPassword*的四种可能设置的行为：

| *pstrUser 名称*  | *pstr密码*  | 发送到 FTP 服务器的用户名 | 发送到 FTP 服务器的密码 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 或""   |   NULL 或""   |         "匿名"         |      用户的电子邮件名称      |
| 非 NULL 字符串 |   NULL 或""   |       *pstrUser 名称*        |             " "             |
|      Null       | 非 NULL 字符串 |            ERROR            |            ERROR            |
| 非 NULL 字符串 | 非 NULL 字符串 |       *pstrUser 名称*        |       *pstr密码*        |

*n波特*<br/>
标识要在服务器上使用的 TCP/IP 端口的数字。

*b被动*<br/>
为此 FTP 会话指定被动或主动模式。 如果设置为 TRUE，它将 Win32 API`dwFlag`设置为INTERNET_FLAG_PASSIVE。

### <a name="return-value"></a>返回值

指向[CFtpConnect](../../mfc/reference/cftpconnection-class.md)对象的指针。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetFtpConnection`连接到 FTP 服务器，并创建并返回指向`CFTPConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如，如果要读取或写入文件，则必须将这些操作作为单独的步骤执行。 有关搜索文件、打开文件以及读取或写入文件的信息，请参阅[CFtpConnect](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)类。 有关执行常见 FTP 连接任务的步骤，请参阅[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)的文章。

### <a name="example"></a>示例

请参阅[CFtpFileFind 的示例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>C 互联网会话：：获取 Gopher 连接

调用此成员函数以建立新的 gopher 连接，并获取指向`CGopherConnection`对象的指针。

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

*pstrUser 名称*<br/>
指向包含用户名的字符串的指针。

*pstr密码*<br/>
指向包含访问密码的字符串的指针。

*n波特*<br/>
标识要在服务器上使用的 TCP/IP 端口的数字。

### <a name="return-value"></a>返回值

指向[Gopher 连接](../../mfc/reference/cgopherconnection-class.md)对象的指针。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetGopherConnection`连接到 gopher 服务器，并创建并返回指向`CGopherConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如，如果要读取或写入数据，则必须将这些操作作为单独的步骤执行。 有关搜索文件、打开文件、读取或写入文件的信息，请参阅类[CGopherConnection、CGopherFile](../../mfc/reference/cgopherconnection-class.md)和[CGopherFileFind。](../../mfc/reference/cgopherfilefind-class.md) [CGopherFile](../../mfc/reference/cgopherfile-class.md) 有关浏览 FTP 网站的信息，请参阅成员函数[OpenURL](#openurl)。 有关执行常见 gopher 连接任务的步骤，请参阅[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)的文章。

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>C 互联网会话：：获取Http连接

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

*n波特*<br/>
标识要在服务器上使用的 TCP/IP 端口的数字。

*pstrUser 名称*<br/>
指向包含用户名的字符串的指针。

*pstr密码*<br/>
指向包含访问密码的字符串的指针。

*dwflags*<br/>
标志的`INTERNET_FLAG_*`任意组合。 请参阅[CHttpConnection：：打开请求的备](../../mfc/reference/chttpconnection-class.md#openrequest)**注**部分中的表，了解*dwFlags*值的说明。

### <a name="return-value"></a>返回值

指向[CHttpConnect](../../mfc/reference/chttpconnection-class.md)对象的指针。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

`GetHttpConnection`连接到 HTTP 服务器，并创建并返回指向`CHttpConnection`对象的指针。 它不在服务器上执行任何特定操作。 例如，如果要查询 HTTP 标头，则必须作为单独的步骤执行此操作。 有关可以使用连接到 HTTP 服务器可以执行的操作的信息，请参阅类[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CHttpFile。](../../mfc/reference/chttpfile-class.md) 有关浏览 HTTP 网站的信息，请参阅成员函数[OpenURL](#openurl)。 有关执行常见 HTTP 连接任务的步骤，请参阅[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)的文章。

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternet 会话：：打开状态回拨

框架将调用此成员函数，以在启用状态回调且操作挂起时更新状态。

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

*dw互联网状态*<br/>
指示进行回调的原因的状态代码。 有关可能值的表，请参阅**备注**。

*lpv状态信息*<br/>
指向缓冲区的指针，其中包含与此回调相关的信息。

*dwStatus 信息长度*<br/>
*lpv状态信息的大小*。

### <a name="remarks"></a>备注

您必须首先调用[启用状态回调](#enablestatuscallback)以利用状态回调。

*dwInternetStatus*参数指示正在执行的操作，并确定*lpvStatus信息*的内容。 *dwStatus信息长度*表示*lpvStatus 信息*中包含的数据的长度。 *dwInternetStatus*的以下状态值定义如下：

|“值”|含义|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|查找*lpvStatus 信息*中包含的名称的 IP 地址。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到*lpvStatus 信息*中包含的名称的 IP 地址。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|连接到以*lpvStatus 信息*指向的套接字地址 （[SOCKADDR](/windows/win32/winsock/sockaddr-2)） 。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|成功连接到*lpvStatus 信息*指向的套接字地址 （SOCKADDR）。|
|INTERNET_STATUS_SENDING_REQUEST|将信息请求发送到服务器。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_REQUEST_SENT|已成功将信息请求发送到服务器。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_RECEIVING_RESPONSE|正在等待服务器响应请求。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功收到来自服务器的响应。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_CLOSING_CONNECTION|关闭与服务器的连接。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_CONNECTION_CLOSED|成功关闭与服务器的连接。 *lpv 状态信息*参数为 NULL。|
|INTERNET_STATUS_HANDLE_CREATED|Win32 API 函数[InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw)用于指示它已创建新句柄。 这允许应用程序调用 Win32 函数[InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle)从另一个线程，如果连接时间过长。 有关这些功能的详细信息，请参阅 Windows SDK。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功终止此句柄值。|

重写此成员函数，以执行状态回调例程之前需要一些操作。

> [!NOTE]
> 状态回调需要线程状态保护。 如果在共享库中使用 MFC，请向重写的开头添加以下行：

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

有关异步操作的详细信息，请参阅文章["Internet 第一步：WinInet](../../mfc/wininet-basics.md)"。

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>C 互联网会话：：打开 URL

调用此成员函数将指定的请求发送到 HTTP 服务器，并允许客户端指定与请求一起发送的其他 RFC822、MIME 或 HTTP 标头。

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
指向开始读取 URL 名称的指针。 仅支持以文件：、ftp：、gopher：或 http： 开头的 URL。 断言如果*pstrURL*为 NULL。

*dwContext*<br/>
使用回调中返回的句柄传递的应用程序定义值。

dwFlags**<br/>
描述如何处理此连接的标志。 有关有效标志的详细信息，请参阅**备注**。 有效标志包括：

- INTERNET_FLAG_TRANSFER_ASCII 默认值。 将文件作为 ASCII 文本传输。

- INTERNET_FLAG_TRANSFER_BINARY将文件作为二进制文件传输。

- INTERNET_FLAG_RELOAD从导线中获取数据，即使它是本地缓存的。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何网关中缓存数据。

- INTERNET_FLAG_SECURE此标志仅适用于 HTTP 请求。 它要求使用安全套接字层或 PCT 在电线上进行安全交易。

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 如果可能，请重用与服务器的现有连接，以访问生成`OpenUrl`的新请求，而不是为每个连接请求创建新会话。

- INTERNET_FLAG_PASSIVE用于 FTP 站点。 使用被动 FTP 语义。 与 的`OpenURL` [CInternet 连接](../../mfc/reference/cinternetconnection-class.md)一起使用。

*pstrHeaders*<br/>
指向包含要发送到 HTTP 服务器的标头的字符串的指针。

*dwHeaders 长度*<br/>
附加标头的长度（以字符表示）。 如果为 -1L，并且*pstrHeader*是非 NULL，则假定*pstrHeader*为零端接，并计算长度。

### <a name="return-value"></a>返回值

仅返回 FTP、GOPHER、HTTP 和 FILE 类型的 Internet 服务的文件句柄。 如果分析不成功，则返回 NULL。

返回的`OpenURL`指针取决于*pstrURL*的服务类型。 下表说明了可以返回的可能指针`OpenURL`。

|URL 类型|返回|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>备注

参数*dwFlags*必须包括INTERNET_FLAG_TRANSFER_ASCII或INTERNET_FLAG_TRANSFER_BINARY，但不能同时包含这两个参数。 其余标志可以与位**或**运算符 **（&#124;**） 组合。

`OpenURL`，它包装 Win32 函数`InternetOpenURL`，只允许从 Internet 服务器下载、检索和读取数据。 `OpenURL`不允许对远程位置进行文件操作，因此不需要[CInternetConnect](../../mfc/reference/cinternetconnection-class.md)对象。

要使用特定于连接（即特定于协议的）函数（如写入文件），必须打开会话，然后打开特定类型的连接，然后使用该连接以所需模式打开文件。 有关`CInternetConnection`特定于连接的功能的详细信息，请参阅。

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>C 互联网会话：：操作员 HINTERNET

使用此运算符获取当前 Internet 会话的 Windows 句柄。

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>C 互联网会话：：SetCookie

为指定的 URL 设置 Cookie。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>参数

*pstrUrl*<br/>
指向 null 端接字符串的指针，用于指定应为其设置 Cookie 的 URL。

*普斯特库奇名称*<br/>
指向包含 Cookie 名称的字符串的指针。

*普斯特库奇数据*<br/>
指向包含要与 URL 关联的实际字符串数据的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。 要获取特定的错误代码，请调用`GetLastError.`

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)的行为，如 Windows SDK 中所述。

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>C 互联网会话：：设置选项

调用此成员函数以设置 Internet 会话的选项。

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
要设置的 Internet 选项。 有关可能的选项的列表，请参阅 Windows SDK 中[的选项标志](/windows/win32/WinInet/option-flags)。

*lpBuffer*<br/>
包含选项设置的缓冲区。

*dwBuffer 长度*<br/>
*lpBuffer*的长度或*dwValue*的大小。

*dwValue*<br/>
包含选项设置的 DWORD。

dwFlags**<br/>
指示各种缓存选项。 默认值设置为 0。 可能的值包括：

- INTERNET_FLAG_DONT_CACHE不要在本地或任何网关服务器中缓存数据。

- INTERNET_FLAG_OFFLINE仅通过持久缓存满足下载操作。 如果缓存中不存在该项目，则返回相应的错误代码。 此标志可与位**或**（ **&#124;**） 运算符组合。

### <a name="return-value"></a>返回值

如果操作成功，则返回 TRUE 的值。 如果发生错误，则返回 FALSE 的值。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttp连接类](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopher 连接类](../../mfc/reference/cgopherconnection-class.md)
