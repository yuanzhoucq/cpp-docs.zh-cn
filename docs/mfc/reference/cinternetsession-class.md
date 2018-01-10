---
title: "CInternetSession 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7aad2f6ce26fd5ca9ed0ec323a8fcb05ac17f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetsession-class"></a>CInternetSession 类
创建和初始化一个或多个同时 Internet 会话，并说明与代理服务器的连接（如果需要）。  
  
## <a name="syntax"></a>语法  
  
```  
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
|[CInternetSession::Close](#close)|当 Internet 会话已终止，则关闭 Internet 连接。|  
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立状态回调例程。|  
|[CInternetSession::GetContext](#getcontext)|当 Internet 会话已终止，则关闭 Internet 连接。|  
|[CInternetSession::GetCookie](#getcookie)|返回指定的 URL 和所有其父级 Url 的 cookie。|  
|[CInternetSession::GetCookieLength](#getcookielength)|检索指定存储在缓冲区中的 cookie 的长度的变量。|  
|[Cinternetsession:: Getftpconnection](#getftpconnection)|打开与服务器的 FTP 会话。 登录用户。|  
|[CInternetSession::GetGopherConnection](#getgopherconnection)|将打开 gopher 服务器的应用程序尝试打开的连接。|  
|[CInternetSession::GetHttpConnection](#gethttpconnection)|打开 HTTP 服务器的应用程序尝试打开的连接。|  
|[CInternetSession::OnStatusCallback](#onstatuscallback)|启用状态回调后，请更新操作的状态。|  
|[Cinternetsession:: Openurl](#openurl)|分析并打开一个 URL。|  
|[CInternetSession::SetCookie](#setcookie)|为指定的 URL 中设置了 cookie。|  
|[CInternetSession::SetOption](#setoption)|设置 Internet 会话选项。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](#operator_hinternet)|当前的 Internet 会话句柄。|  
  
## <a name="remarks"></a>备注  
 如果应用程序的持续时间内，必须维护你的 Internet 连接，则可以创建`CInternetSession`类的成员[CWinApp](../../mfc/reference/cwinapp-class.md)。  
  
 一旦已建立 Internet 会话，就可以调用[OpenURL](#openurl)。 `CInternetSession`然后为您分析该 URL，通过调用全局函数[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)。 而不考虑其协议类型、`CInternetSession`解释 URL，并为你管理。 它可以处理针对与 URL 资源"file://"标识的本地文件的请求。 `OpenURL`将返回一个指向[CStdioFile](../../mfc/reference/cstdiofile-class.md)如果名称传递给它的对象是本地文件。  
  
 如果打开上 Internet 服务器使用的 URL `OpenURL`，你可以从网站读取信息。 如果你想要在文件位于服务器上执行的特定于服务 （如 HTTP、 FTP 或 gopher） 操作，必须建立与该服务器适当的连接。 若要打开特定种类的直接到特定服务的连接，请使用以下成员函数之一：  
  
- [GetGopherConnection](#getgopherconnection)以打开 gopher 服务的连接。  
  
- [GetHttpConnection](#gethttpconnection)打开对 HTTP 服务的连接。  
  
- [GetFtpConnection](#getftpconnection)以打开与 FTP 服务建立连接。  
  
 [SetOption](#setoption)允许你设置查询选项的会话中，如超时值的重试次数，依次类推。  
  
 `CInternetSession`成员函数[SetCookie](#setcookie)， [GetCookie](#getcookie)，和[GetCookieLength](#getcookielength)提供用于管理 Win32 cookie 数据库，通过该服务器和脚本维护的方法有关客户端工作站的状态信息。  
  
 有关基本 Internet 编程任务的详细信息，请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)。 有关使用 MFC WinInet 类的常规信息，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
> [!NOTE]
> `CInternetSession`将引发[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)为不受支持的服务类型。 当前支持只能使用以下服务类型： FTP、 HTTP、 gopher 和文件。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxinet.h  
  
##  <a name="cinternetsession"></a>CInternetSession::CInternetSession  
 此成员函数调用时`CInternetSession`创建对象。  
  
```  
CInternetSession(
    LPCTSTR pstrAgent = NULL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,  
    LPCTSTR pstrProxyName = NULL,  
    LPCTSTR pstrProxyBypass = NULL,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `pstrAgent`  
 指向用于标识应用程序或调用 Internet 函数 （例如，"Microsoft Internet 浏览器"） 的实体的名称的字符串的指针。 如果`pstrAgent`是**NULL** （默认值） 时，框架会调用全局函数[AfxGetAppName](application-information-and-management.md#afxgetappname)，这将返回包含应用程序的名称的以 null 结尾的字符串。 某些协议使用此字符串来标识应用程序到服务器。  
  
 `dwContext`  
 操作上下文标识符。 `dwContext`标识返回的操作的状态信息[CInternetSession::OnStatusCallback](#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 对象和做的任何工作将与该上下文 id。  
  
 `dwAccessType`  
 所需访问权限的类型。 以下是有效的值，可以提供一种：  
  
- **INTERNET_OPEN_TYPE_PRECONFIG**连接使用注册表中的预配置的设置。 此访问类型被设置为默认值。 若要连接通过 TIS 代理，设置`dwAccessType`为此值; 你然后注册表正确设置。  
  
- `INTERNET_OPEN_TYPE_DIRECT`直接连接到 Internet。  
  
- `INTERNET_OPEN_TYPE_PROXY`连接通过 CERN 代理。  
  
 有关如何通过不同类型的代理的连接的信息，请参阅[典型 FTP 客户端应用程序中的步骤](../../mfc/steps-in-a-typical-ftp-client-application.md)。  
  
 *pstrProxyName*  
 首选 CERN 代理服务器的名称如果`dwAccessType`被设置为`INTERNET_OPEN_TYPE_PROXY`。 默认值是**NULL**。  
  
 *pstrProxyBypass*  
 指向包含的服务器地址的可选列表的字符串的指针。 使用代理服务器访问时，可能会绕过这些地址。 如果**NULL**提供值，将从注册表中读取跳过列表。 此参数是有意义才`dwAccessType`设置为`INTERNET_OPEN_TYPE_PROXY`。  
  
 `dwFlags`  
 指示各种缓存选项。 默认值设置为 0。 可能的值包括：  
  
- `INTERNET_FLAG_DONT_CACHE`本地或在任何网关服务器，则不缓存数据。  
  
- `INTERNET_FLAG_OFFLINE`下载操作通过永久性缓存仅对结果满意。 如果在缓存中不存在此项，则返回相应的错误代码。 此标志可以与的按位组合`OR`( **&#124;**) 运算符。  
  
### <a name="remarks"></a>备注  
 **CInternetSession**是由应用程序调用的第一个 Internet 函数。 它将初始化内部数据结构，并为将来的调用，从应用程序做好准备。  
  
 如果可以打开无 Internet 连接，`CInternetSession`引发[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。  
  
### <a name="example"></a>示例  
  请参阅示例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="close"></a>CInternetSession::Close  
 调用此成员函数，你的应用程序完成后使用`CInternetSession`对象。  
  
```  
virtual void Close();
```  
  
### <a name="example"></a>示例  
  请参阅示例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback  
 调用此成员函数以启用状态回调。  
  
```  
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是启用还是禁用回调。 默认值是**TRUE**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 处理时状态回调，你可以在应用程序的状态栏中提供有关操作的操作 （如名称解析，连接到服务器上，依次类推） 的进度的状态。 显示操作状态时尤其需要长期操作。  
  
 因为回调在请求处理期间发生，应用程序应该花尽可能回调，以防止数据吞吐量下降到网络中的最小时间。 例如，将出现一个对话框，在回调中可能是此类较长的操作，服务器终止请求。  
  
 无法删除状态回调，只要任何回调处于挂起状态。  
  
 若要以异步方式处理的任何操作，必须创建你自己的线程，或使用无需 MFC WinInet 函数中。  
  
##  <a name="getcontext"></a>CInternetSession::GetContext  
 调用此成员函数可获取特定应用程序会话的上下文值。  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>返回值  
 应用程序定义的上下文标识符。  
  
### <a name="remarks"></a>备注  
 [OnStatusCallback](#onstatuscallback)使用返回的上下文 ID **GetContext**来报告特定应用程序的状态。 例如，当用户激活涉及返回状态信息的 Internet 请求，状态回调会使用该特定请求报告状态的上下文 ID。 如果用户激活两个单独 Internet 请求，两者都涉及返回状态信息`OnStatusCallback`上下文标识符用于返回有关其相应的请求的状态。 因此，该上下文标识符用于所有的状态回调操作，并且与该会话，直到在会话结束相关联。  
  
 有关异步操作的详细信息，请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)。  
  
##  <a name="getcookie"></a>CInternetSession::GetCookie  
 此成员函数实现的 Win32 函数的行为[InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710)，如 Windows SDK 中所述。  
  
```  
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
 `pstrUrl`  
 指向包含 URL 的字符串的指针。  
  
 `pstrCookieName`  
 指向包含要获取为指定的 URL 的 cookie 的名称的字符串的指针。  
  
 `pstrCookieData`  
 在第一个重载中，指向包含接收的 cookie 数据的缓冲区的地址的字符串的指针。 此值可为**NULL**。 在第二个重载中，对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象以便接收的 cookie 数据。  
  
 `dwBufLen`  
 指定的大小变量`pstrCookieData`缓冲区。 如果函数成功，缓冲区接收复制到的数据量`pstrCookieData`缓冲区。 如果`pstrCookieData`是**NULL**，该参数会接收一个值，指定所需的所有 cookie 数据复制的缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果成功，或**FALSE**否则为。 如果调用失败，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以确定错误的原因。 应用以下的错误值：  
  
- **ERROR_NO_MORE_ITEMS**没有为指定的 URL 的任何 cookie，并且所有父级。  
  
- **ERROR_INSUFFICIENT_BUFFER**中传递的值`dwBufLen`不足，无法将复制所有 cookie 数据。 返回的值`dwBufLen`方案来获取所有数据缓冲区的大小。  
  
### <a name="remarks"></a>备注  
 在第二个重载中，MFC cookie 数据检索到所提供`CString`对象。  
  
##  <a name="getcookielength"></a>CInternetSession::GetCookieLength  
 调用此成员函数可获取存储在缓冲区中的 cookie 的长度。  
  
```  
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName);
```  
  
### <a name="parameters"></a>参数  
 `pstrUrl`  
 指向包含 URL 的字符串的指针  
  
 `pstrCookieName`  
 指向包含的 cookie 名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 A`DWORD`值，该值指示该 cookie，存储在缓冲区中的长度。 如果任何 cookie 零由同名`pstrCookieName`存在。  
  
### <a name="remarks"></a>备注  
 使用此值[GetCookie](#getcookie)。  
  
##  <a name="getftpconnection"></a>Cinternetsession:: Getftpconnection  
 调用此成员函数以建立 FTP 连接并获取指向的指针`CFtpConnection`对象。  
  
```  
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `pstrServer`  
 指向包含 FTP 服务器名称的字符串的指针。  
  
 `pstrUserName`  
 指向以 null 结尾的字符串，指定要登录的用户的名称。 如果**NULL**，默认值是匿名的。  
  
 `pstrPassword`  
 指向一个以 null 结尾的字符串，指定要用于登录的密码的指针。 如果这两个`pstrPassword`和`pstrUserName`是**NULL**，默认匿名密码是用户的电子邮件名称。 如果`pstrPassword`是**NULL** （或空字符串），但`pstrUserName`不**NULL**，使用空白密码。 下表描述的四个可能的设置的行为`pstrUserName`和`pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|"匿名"|用户的电子邮件名称|  
|非- **NULL**字符串|**NULL**或""|`pstrUserName`|" "|  
|**NULL**非**NULL**字符串|**错误**|**错误**||  
|非- **NULL**字符串|非- **NULL**字符串|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 一个数字，标识要使用服务器上的 TCP/IP 端口。  
  
 `bPassive`  
 为此 FTP 会话指定被动还是主动模式。 如果设置为**TRUE**，它将设置 Win32 API`dwFlag`到**INTERNET_FLAG_PASSIVE**。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CFtpConnection](../../mfc/reference/cftpconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `GetFtpConnection`连接到 FTP 服务器，并创建并返回一个指向**CFTPConnection**对象。 它不执行任何服务器上的特定操作。 如果你想要读取或写入到文件，例如，必须执行这些操作作为单独的步骤。 请参阅类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)有关搜索文件，打开文件、 和读取或写入文件。 请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)中执行常见的 FTP 连接任务的步骤。  
  
### <a name="example"></a>示例  
  请参阅示例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection  
 调用此成员函数建立新的 gopher 连接，获取一个指向`CGopherConnection`对象。  
  
```  
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>参数  
 `pstrServer`  
 指向包含 gopher 服务器名称的字符串的指针。  
  
 `pstrUserName`  
 指向包含的用户名称的字符串的指针。  
  
 `pstrPassword`  
 指向包含的访问密码的字符串的指针。  
  
 `nPort`  
 一个数字，标识要使用服务器上的 TCP/IP 端口。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `GetGopherConnection`连接到 gopher 服务器，并创建并返回一个指向`CGopherConnection`对象。 它不执行任何服务器上的特定操作。 如果你想要读取或写入数据，例如，必须执行这些操作作为单独的步骤。 请参阅类[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)， [CGopherFile](../../mfc/reference/cgopherfile-class.md)，和[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)有关搜索文件，打开文件、 和读取或写入文件。 关于浏览 FTP 站点的信息，请参阅成员函数[OpenURL](#openurl)。 请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)中执行常见 gopher 连接任务的步骤。  
  
##  <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection  
 调用此成员函数以建立 HTTP 连接并获取指向的指针`CHttpConnection`对象。  
  
```  
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
 `pstrServer`  
 指向包含 HTTP 服务器名称的字符串的指针。  
  
 `nPort`  
 一个数字，标识要使用服务器上的 TCP/IP 端口。  
  
 `pstrUserName`  
 指向包含的用户名称的字符串的指针。  
  
 `pstrPassword`  
 指向包含的访问密码的字符串的指针。  
  
 *dwflags*  
 任意组合**INTERNET_ FLAG_\*** 标志。 请参阅中的表**备注**部分[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)有关的说明`dwFlags`值。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `GetHttpConnection`连接到 HTTP 服务器，并创建，并返回一个指向`CHttpConnection`对象。 它不执行任何服务器上的特定操作。 如果你想要查询 HTTP 标头，例如，必须执行此操作作为一个单独的步骤。 请参阅类[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md)有关操作的信息可通过使用与 HTTP 服务器的连接执行。 关于浏览 HTTP 站点的信息，请参阅成员函数[OpenURL](#openurl)。 请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)中执行常见的 HTTP 连接任务的步骤。  
  
##  <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback  
 由框架更新的状态，启用状态回调和操作处于挂起状态时调用此成员函数。  
  
```  
virtual void OnStatusCallback(
    DWORD_PTR dwContext,  
    DWORD dwInternetStatus,  
    LPVOID lpvStatusInformation,  
    DWORD dwStatusInformationLength);
```  
  
### <a name="parameters"></a>参数  
 `dwContext`  
 应用程序提供的上下文值。  
  
 `dwInternetStatus`  
 状态代码，它指示正在进行回调的原因。 请参阅**备注**有关可能的值的表。  
  
 `lpvStatusInformation`  
 指向包含与此回调相关的信息的缓冲区的指针。  
  
 `dwStatusInformationLength`  
 `lpvStatusInformation` 的大小。  
  
### <a name="remarks"></a>备注  
 必须先调用[EnableStatusCallback](#enablestatuscallback)要利用的状态回调。  
  
 `dwInternetStatus`参数指示正在执行的操作，并确定的内容`lpvStatusInformation`将。 `dwStatusInformationLength`指示中包括的数据的长度`lpvStatusInformation`。 以下状态的值`dwInternetStatus`，如下所示定义：  
  
|“值”|含义|  
|-----------|-------------|  
|`INTERNET_STATUS_RESOLVING_NAME`|查找名称中包含的 IP 地址`lpvStatusInformation`。|  
|`INTERNET_STATUS_NAME_RESOLVED`|已成功找到中包含的名称的 IP 地址`lpvStatusInformation`。|  
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|连接到的套接字地址 ( [SOCKADDR](../../mfc/reference/sockaddr-structure.md)) 指向`lpvStatusInformation`。|  
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|已成功连接到的套接字地址 ( `SOCKADDR`) 指向`lpvStatusInformation`。|  
|`INTERNET_STATUS_SENDING_REQUEST`|向服务器发送信息请求。 `lpvStatusInformation`参数是**NULL**。|  
|**INTERNET_STATUS_ REQUEST_SENT**|已成功发送到服务器的信息请求。 `lpvStatusInformation`参数是**NULL**。|  
|`INTERNET_STATUS_RECEIVING_RESPONSE`|正在等待服务器响应请求。 `lpvStatusInformation`参数是**NULL**。|  
|`INTERNET_STATUS_RESPONSE_RECEIVED`|已成功从服务器收到的响应。 `lpvStatusInformation`参数是**NULL**。|  
|`INTERNET_STATUS_CLOSING_CONNECTION`|关闭到服务器的连接。 `lpvStatusInformation`参数是**NULL**。|  
|`INTERNET_STATUS_CONNECTION_CLOSED`|已成功关闭了连接到服务器。 `lpvStatusInformation`参数是**NULL**。|  
|`INTERNET_STATUS_HANDLE_CREATED`|使用 Win32 API 函数[InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363)以指示它已创建新的句柄。 这允许应用程序调用 Win32 函数[InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350)从另一个线程，如果连接时间太长。 请参阅 Windows SDKfor 有关这些函数的详细信息。|  
|`INTERNET_STATUS_HANDLE_CLOSING`|已成功终止此句柄值。|  
  
 重写该成员函数以之前执行的状态回调例程需要执行一些操作。  
  
> [!NOTE]
>  状态回调需要线程状态保护。 如果在共享库中使用 MFC，请重写的开头添加以下行：  
  
 [!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]  
  
 有关异步操作的详细信息，请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)。  
  
##  <a name="openurl"></a>Cinternetsession:: Openurl  
 调用此成员函数将指定的请求发送到 HTTP 服务器，并允许客户端指定其他 RFC822 MIME 或要连同请求一起发送 HTTP 标头。  
  
```  
CStdioFile* OpenURL(
    LPCTSTR pstrURL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,  
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLength = 0);
```  
  
### <a name="parameters"></a>参数  
 *pstrURL*  
 指向要开始读取的 url 的名称的指针。 仅 Url 开头文件:，ftp:，gopher:，或 http： 支持。 **Assert 语句**如果*pszURL*是**NULL**。  
  
 `dwContext`  
 使用回调中返回的句柄传递应用程序定义的值。  
  
 `dwFlags`  
 描述如何处理此连接的标志。 请参阅**备注**有关有效的标志的详细信息。 有效标志包括：  
  
- **INTERNET_FLAG_TRANSFER_ASCII**默认值。 将文件传输为 ASCII 文本。  
  
- **INTERNET_FLAG_TRANSFER_BINARY**传输该文件为二进制文件。  
  
- `INTERNET_FLAG_RELOAD`即使本地缓存，请从网络中获取数据。  
  
- `INTERNET_FLAG_DONT_CACHE`本地或在任何网关，则不缓存数据。  
  
- `INTERNET_FLAG_SECURE`此标志将适用于仅 HTTP 请求。 它会请求使用安全套接字层或百分比在网络上的安全事务  
  
- **INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT**如果可能，请重复使用的生成的新请求服务器的现有连接**OpenUrl**而不是创建每个连接请求的新会话。  
  
- **INTERNET_FLAG_PASSIVE**用于 FTP 站点。 使用被动 FTP 语义。 与使用[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)的`OpenURL`。  
  
 `pstrHeaders`  
 指向包含要发送到 HTTP 服务器的标头的字符串的指针。  
  
 *dwHeadersLength*  
 以字符为单位，其他标头的长度。 如果这是-1l 和`pstrHeaders`为非**NULL**，然后`pstrHeaders`假定为零终止，并计算长度。  
  
### <a name="return-value"></a>返回值  
 返回 FTP、 GOPHER、 HTTP 和文件类型 Internet 服务的文件句柄。 返回**NULL**如果分析失败。  
  
 指针的`OpenURL`取决于返回*pszURL*的服务类型。 下表说明了可能的指针`OpenURL`可以返回。  
  
|URL 类型|返回|  
|--------------|-------------|  
|file://|**CStdioFile\***|  
|http://|**CHttpFile\***|  
|gopher://|**CGopherFile\***|  
|ftp: / /|**CInternetFile\***|  
  
### <a name="remarks"></a>备注  
 参数`dwFlags`必须包括**INTERNET_FLAG_TRANSFER_ASCII**或**INTERNET_FLAG_TRANSFER_BINARY**，但不是两者。 可以与的按位组合的剩余标志`OR`运算符 ( **&#124;**)。  
  
 `OpenURL`其包装的 Win32 函数**InternetOpenURL**，允许仅下载、 检索和从 Internet 服务器读取数据。 `OpenURL`允许远程位置上的没有对文件进行操作，因此它需要否[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)对象。  
  
 若要使用特定于连接的 (即，特定于协议的) 函数，如对文件进行写入，你必须打开会话，然后打开特定种类的连接，然后使用该连接所需模式中打开文件。 请参阅`CInternetConnection`有关特定于连接的函数的详细信息。  
  
##  <a name="operator_hinternet"></a>CInternetSession::operator HINTERNET  
 使用此运算符将获取当前的 Internet 会话的 Windows 句柄。  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="setcookie"></a>CInternetSession::SetCookie  
 为指定的 URL 中设置了 cookie。  
  
```  
static BOOL SetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPCTSTR pstrCookieData);
```  
  
### <a name="parameters"></a>参数  
 `pstrUrl`  
 一个以 null 结尾的字符串，指定应为其设置 cookie 的 URL 指向的指针。  
  
 `pstrCookieName`  
 指向包含的 cookie 名称的字符串的指针。  
  
 `pstrCookieData`  
 指向包含要替换的 URL 关联的实际字符串数据的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果成功，或**FALSE**否则为。 若要获取特定的错误代码，调用**时出错。**  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107)，如 Windows SDK 中所述。  
  
##  <a name="setoption"></a>CInternetSession::SetOption  
 调用此成员函数以设置 Internet 会话选项。  
  
```  
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
 `dwOption`  
 要设置的 Internet 选项。 请参阅[选项标志](http://msdn.microsoft.com/library/windows/desktop/aa385328)Windows SDKfor 的可能的选项列表中。  
  
 `lpBuffer`  
 包含的选项设置的缓冲区。  
  
 *dwBufferLength*  
 长度`lpBuffer`或的大小`dwValue`。  
  
 `dwValue`  
 A `DWORD` ，其中包含的选项设置。  
  
 `dwFlags`  
 指示各种缓存选项。 默认值设置为 0。 可能的值包括：  
  
- `INTERNET_FLAG_DONT_CACHE`本地或在任何网关服务器，则不缓存数据。  
  
- `INTERNET_FLAG_OFFLINE`下载操作通过永久性缓存仅对结果满意。 如果在缓存中不存在此项，则返回相应的错误代码。 此标志可以与的按位组合`OR`( **&#124;**) 运算符。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，值为**TRUE**返回。 如果出现了错误，值为**FALSE**返回。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection 类](../../mfc/reference/cgopherconnection-class.md)
