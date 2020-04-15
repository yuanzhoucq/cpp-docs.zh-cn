---
title: CGopher 连接类
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
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373712"
---
# <a name="cgopherconnection-class"></a>CGopher 连接类

管理与 Gopher Internet 服务器的连接。

> [!NOTE]
> 类`CGopherConnection` `CGopherFile`、 `CGopherFileFind`、`CGopherLocator`及其成员已被弃用，因为它们在 Windows XP 平台上不工作，但它们将继续在较早的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Gopher 连接：：Cgopher 连接](#cgopherconnection)|构造 `CGopherConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[Gopher 连接：：创建定位器](#createlocator)|创建一个[CGopherLocator 对象](../../mfc/reference/cgopherlocator-class.md)来查找 gopher 服务器上的文件。|
|[Gopher 连接：获取属性](#getattribute)|检索有关 gopher 对象的属性信息。|
|[Gopher 连接：：打开文件](#openfile)|打开一个 gopher 文件。|

## <a name="remarks"></a>备注

gopher 服务是 MFC WinInet 类认可的三种互联网服务之一。

该类`CGopherConnection`包含一个构造函数和三个管理 gopher 服务的附加成员函数[：OpenFile、CreateLocator](#openfile)和[CreateLocator](#createlocator)[GetAttribute](#getattribute)。

要与 gopher Internet 服务器通信，必须首先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例，然后调用[CInternetSession：：getGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，`CGopherConnection`它创建对象并返回指向它的指针。 您从不直接创建`CGopherConnection`对象。

要了解有关如何`CGopherConnection`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。 有关使用其他两个受支持的 Internet 服务的详细信息，FTP 和 HTTP 请参阅[类 CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 互联网连接](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>Gopher 连接：：Cgopher 连接

调用此成员函数以构造对象`CGopherConnection`。

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

### <a name="remarks"></a>备注

您从不直接创建`CGopherConnection`。 相反，调用[CInternetSession：：GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，它`CGopherConnection`创建一个对象并返回指向它的指针。

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>Gopher 连接：：创建定位器

调用此成员函数以创建 gopher 定位器以查找或标识 gopher 服务器上的文件。

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
指向要检索的 gopher 文档或目录名称的字符串的指针。 如果*pstrDisplayString*参数为 NULL，则返回 gopher 服务器的默认目录。

*pstrSelectorString*<br/>
指向要发送到 gopher 服务器以检索项的选择器字符串的指针。 *pstrSelectorString*可以是 NULL。

*dwGopher类型*<br/>
这指定*pstrSelectorString*是否引用目录或文档，以及请求是 gopher 还是 gopher*。 请参阅 Windows SDK 中[结构GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw)的属性。

*pstrLocator*<br/>
指向标识要打开的文件的字符串的指针。 通常，此字符串是从调用[CGopherFileFind 返回：getLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。

*pstrServer 名称*<br/>
指向包含 gopher 服务器名称的字符串的指针。

*n波特*<br/>
标识此连接的 Internet 端口的编号。

### <a name="return-value"></a>返回值

[Gopher 定位器](../../mfc/reference/cgopherlocator-class.md)对象。

### <a name="remarks"></a>备注

成员函数的静态版本要求您指定服务器，而非静态版本使用连接对象的服务器名称。

为了从 gopher 服务器检索信息，应用程序必须首先获取 gopher 定位器。 然后，应用程序必须将定位器视为不透明令牌（即，应用程序可以使用定位器，但不能直接操作或比较它）。 通常，应用程序使用定位器调用[CGopherFileFind：：FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成员函数来检索特定信息。

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>Gopher 连接：获取属性

调用此成员函数从 gopher 服务器检索有关项目的特定属性信息。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>参数

*参考定位器*<br/>
对[CGopher 定位器对象的引用](../../mfc/reference/cgopherlocator-class.md)。

*str被请求属性*<br/>
指定请求属性名称的空间分隔字符串。

*strResult*<br/>
对接收定位器类型的[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>Gopher 连接：：打开文件

调用此成员函数以在 gopher 服务器上打开文件。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*参考定位器*<br/>
对[CGopher 定位器对象的引用](../../mfc/reference/cgopherlocator-class.md)。

dwFlags**<br/>
INTERNET_FLAG_* 标志的任意组合。 有关INTERNET_FLAG_\*标志的详细信息，请参阅[CInternetSession：：OpenUrl。](../../mfc/reference/cinternetsession-class.md#openurl)

*pstrView*<br/>
指向文件视图字符串的指针。 如果服务器中存在该文件的多个视图，则此参数指定要打开的文件视图。 如果*pstrView*为 NULL，则使用默认文件视图。

*dwContext*<br/>
正在打开的文件的上下文 ID。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="return-value"></a>返回值

指向要打开[的 CGopherFile](../../mfc/reference/cgopherfile-class.md)对象的指针。

### <a name="remarks"></a>备注

覆盖*dwContext*默认值，将上下文标识符设置为您选择的值。 上下文标识符与其`CGopherConnection`[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession：：onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供标识该值的操作的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="see-also"></a>另请参阅

[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttp连接类](../../mfc/reference/chttpconnection-class.md)<br/>
[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[C 互联网会话类](../../mfc/reference/cinternetsession-class.md)
