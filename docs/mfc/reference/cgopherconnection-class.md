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
ms.openlocfilehash: f9c2a99c30213a28f4c20ba0f4a2eebea85bef76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519660"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 类

管理与 Gopher Internet 服务器的连接。

> [!NOTE]
>  类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和它们的成员具有已弃用，因为它们不能在 Windows XP 平台上，但它们将继续在早期版本的平台上工作。

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
|[CGopherConnection::CreateLocator](#createlocator)|创建[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)要查找 gopher 服务器上的文件对象。|
|[CGopherConnection::GetAttribute](#getattribute)|检索有关 gopher 对象的属性信息。|
|[CGopherConnection::OpenFile](#openfile)|打开 gopher 文件。|

## <a name="remarks"></a>备注

Gopher 服务是可识别的 MFC WinInet 类的三个 Internet 服务之一。

该类`CGopherConnection`包含一个构造函数和管理 gopher 服务的三个其他成员函数： [OpenFile](#openfile)， [CreateLocator](#createlocator)，并[GetAttribute](#getattribute).

若要与 gopher Internet 服务器进行通信，必须首先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后调用[cinternetsession:: Getgopherconnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，这将创建`CGopherConnection`对象，并返回的指针。 永远不会创建`CGopherConnection`直接对象。

若要详细了解如何`CGopherConnection`适用于其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 详细了解使用其他两个支持的 Internet 服务，FTP 和 HTTP 请参见类[CHttpConnection](../../mfc/reference/chttpconnection-class.md)并[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

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
一个指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。

*hConnected*<br/>
当前 Internet 会话的 Windows 句柄。

*pstrServer*<br/>
指向包含 FTP 服务器名称的字符串的指针。

*dwContext*<br/>
操作的上下文标识符。 *dwContext*标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 将与该上下文 id。 关联的对象以及它执行任何工作

*pstrUserName*<br/>
指向一个以 null 结尾的字符串，指定要登录的用户的名称。 如果为 NULL，则默认值是匿名的。

*pstrPassword*<br/>
一个指向一个以 null 结尾的字符串，指定要用于登录的密码。 如果这两个*pstrPassword*并*pstrUserName*为 NULL 时，默认匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL （或空字符串），但*pstrUserName*不为 NULL，则使用空密码。 下表描述了四个可能的设置的行为*pstrUserName*并*pstrPassword*:

|*pstrUserName*|*pstrPassword*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|用户的电子邮件名称|
|非 NULL 字符串|NULL 或""|*pstrUserName*|" "|
|NULL 非空字符串|错误|错误||
|非 NULL 字符串|非 NULL 字符串|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
标识要在服务器上使用的 TCP/IP 端口号。

### <a name="remarks"></a>备注

永远不会创建`CGopherConnection`直接。 而是调用[cinternetsession:: Getgopherconnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，这将创建`CGopherConnection`对象并返回的指针。

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

调用此成员函数以创建 gopher 定位符以找到或识别 gopher 服务器上的文件。

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
指向包含要检索的目录的 gopher 文档的名称的字符串的指针。 如果*pstrDisplayString*参数为 NULL，则返回 gopher 服务器的默认目录。

*pstrSelectorString*<br/>
指向要发送到 gopher 服务器以检索项的选择器字符串的指针。 *pstrSelectorString*可以为 NULL。

*dwGopherType*<br/>
这会指定是否*pstrSelectorString*指的是目录或文档，以及该请求是 gopher +。 查看结构的属性[GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) Windows SDK 中。

*pstrLocator*<br/>
指向标识要打开的文件的字符串的指针。 通常情况下，此字符串返回通过调用[CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。

*pstrServerName*<br/>
指向包含 gopher 服务器名称的字符串的指针。

*nPort*<br/>
标识此连接的 Internet 端口的编号。

### <a name="return-value"></a>返回值

一个[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

### <a name="remarks"></a>备注

成员函数的静态版本，需要指定服务器，而非静态版本使用的连接对象中的服务器名称。

若要从 gopher 服务器检索信息，应用程序必须先获取 gopher 定位符。 应用程序然后必须将定位符视为不透明的令牌 （即，应用程序可以使用定位符，但不能直接操作或将其进行比较）。 通常情况下，应用程序对的调用使用定位符[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成员函数以检索特定的信息。

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

调用此成员函数以从 gopher 服务器中检索有关某个项的特定属性信息。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>参数

*refLocator*<br/>
对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

*strRequestedAttributes*<br/>
指定请求的属性的名称以空格分隔的字符串。

*strResult*<br/>
对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收定位符类型。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。

##  <a name="openfile"></a>  CGopherConnection::OpenFile

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
对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

*dwFlags*<br/>
INTERNET_FLAG_ * 标志的任意组合。 请参阅[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)有关进一步信息 INTERNET_FLAG_\*标志。

*pstrView*<br/>
指向文件视图字符串的指针。 如果在服务器上存在多个文件的视图，此参数指定要打开文件视图。 如果*pstrView*为 NULL，使用默认文件视图。

*dwContext*<br/>
所打开的文件上下文 ID。 请参阅**备注**有关详细信息*dwContext*。

### <a name="return-value"></a>返回值

一个指向[CGopherFile](../../mfc/reference/cgopherfile-class.md)对象打开。

### <a name="remarks"></a>备注

重写*dwContext*默认可为您选择的值设置的上下文标识符。 上下文标识符是否与此特定操作相关联`CGopherConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

## <a name="see-also"></a>请参阅

[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
