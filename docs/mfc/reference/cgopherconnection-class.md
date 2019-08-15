---
title: CGopherConnection 类
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506195"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 类

管理与 Gopher Internet 服务器的连接。

> [!NOTE]
>  类`CGopherConnection`、 `CGopherFile`、和其成员`CGopherLocator`已被弃用, 因为它们不能在 Windows XP 平台上运行, 但它们将继续在早期的平台上工作。 `CGopherFileFind`

## <a name="syntax"></a>语法

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|构造 `CGopherConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|创建一个[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象以在 gopher 服务器上查找文件。|
|[CGopherConnection::GetAttribute](#getattribute)|检索有关 gopher 对象的特性信息。|
|[CGopherConnection::OpenFile](#openfile)|打开 gopher 文件。|

## <a name="remarks"></a>备注

Gopher 服务是由 MFC WinInet 类识别的三个 Internet 服务之一。

类`CGopherConnection`包含构造函数和其他三个用于管理 gopher 服务的成员函数:[OpenFile](#openfile)、 [CreateLocator](#createlocator)和[GetAttribute](#getattribute)。

若要与 gopher Internet 服务器通信, 必须先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例, 然后调用[CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), `CGopherConnection`这将创建对象并返回指向该对象的指针。 永远不会直接`CGopherConnection`创建对象。

若要了解有关如何`CGopherConnection`使用其他 MFC Internet 类的详细信息, 请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。 有关使用其他两个受支持的 Internet 服务的详细信息, 请参阅[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>要求

**标头:** afxinet。h

##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

调用此成员函数来构造`CGopherConnection`对象。

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
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

### <a name="remarks"></a>备注

永远不会`CGopherConnection`直接创建。 相反, 可以调用[CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), 它将`CGopherConnection`创建一个对象并返回指向该对象的指针。

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

调用此成员函数以创建一个 gopher 定位符, 以查找或标识 gopher 服务器上的文件。

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>参数

*pstrDisplayString*<br/>
指向字符串的指针, 该字符串包含要检索的 gopher 文档或目录的名称。 如果*pstrDisplayString*参数为 NULL, 则返回 gopher 服务器的默认目录。

*pstrSelectorString*<br/>
指向要发送到 gopher 服务器以便检索项的选择器字符串的指针。 *pstrSelectorString*可以为 NULL。

*dwGopherType*<br/>
这将指定*pstrSelectorString*是指目录还是文档, 以及请求是 gopher 还是 gopher +。 请参阅 Windows SDK 中结构[GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw)的属性。

*pstrLocator*<br/>
指向字符串的指针, 该字符串标识要打开的文件。 通常, 此字符串从对[CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)的调用返回。

*pstrServerName*<br/>
指向包含 gopher 服务器名称的字符串的指针。

*nPort*<br/>
标识此连接的 Internet 端口的编号。

### <a name="return-value"></a>返回值

一个[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

### <a name="remarks"></a>备注

成员函数的静态版本要求你指定服务器, 而非静态版本则使用连接对象中的服务器名称。

为了从 gopher 服务器中检索信息, 应用程序必须首先获取 gopher 定位符。 然后, 应用程序必须将定位符视为不透明标记 (即, 应用程序可以使用定位符, 但不能直接对其进行操作或比较)。 通常, 应用程序使用定位符对[CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成员函数进行调用以检索特定的信息片段。

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

调用此成员函数以从 gopher 服务器检索有关项的特定特性信息。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>参数

*refLocator*<br/>
对[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象的引用。

*strRequestedAttributes*<br/>
用空格分隔的字符串, 用于指定所请求的属性的名称。

*strResult*<br/>
对接收定位符类型的[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

##  <a name="openfile"></a>CGopherConnection:: OpenFile

调用此成员函数以打开 gopher 服务器上的文件。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*refLocator*<br/>
对[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象的引用。

*dwFlags*<br/>
INTERNET_FLAG_ * 标志的任意组合。 有关 INTERNET_FLAG_\*标志的详细信息, 请参阅[CInternetSession:: OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) 。

*pstrView*<br/>
指向文件视图字符串的指针。 如果服务器上存在文件的多个视图, 则此参数指定要打开的文件视图。 如果*pstrView*为 NULL, 则使用默认文件视图。

*dwContext*<br/>
正在打开的文件的上下文 ID。 有关*dwContext*的详细信息, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

指向要打开的[CGopherFile](../../mfc/reference/cgopherfile-class.md)对象的指针。

### <a name="remarks"></a>备注

重写*dwContext*默认值, 以将上下文标识符设置为你选择的值。 上下文标识符与`CGopherConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以提供用于标识该操作的状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

## <a name="see-also"></a>请参阅

[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
