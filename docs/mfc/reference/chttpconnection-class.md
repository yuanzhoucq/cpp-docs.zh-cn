---
title: CHttpConnection 类
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425891"
---
# <a name="chttpconnection-class"></a>CHttpConnection 类

管理与 HTTP 服务器的连接。

## <a name="syntax"></a>语法

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHttpConnection：： CHttpConnection](#chttpconnection)|创建一个 `CHttpConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHttpConnection：： OpenRequest](#openrequest)|打开 HTTP 请求。|

## <a name="remarks"></a>备注

HTTP 是由 MFC WinInet 类实现的三个 Internet 服务器协议之一。

类 `CHttpConnection` 包含构造函数和一个成员函数[OpenRequest](#openrequest)，该函数使用 HTTP 协议管理与服务器的连接。

若要与 HTTP 服务器通信，必须先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例，然后创建[CHttpConnection](#chttpconnection)对象。 永远不会直接创建 `CHttpConnection` 对象;相反，可以调用[CInternetSession：： GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，它将创建 `CHttpConnection` 对象并返回一个指向该对象的指针。

若要详细了解 `CHttpConnection` 如何与其他 MFC Internet 类结合使用，请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。 有关使用其他两个受支持的 Internet 协议（gopher 和 FTP）连接到服务器的详细信息，请参阅类[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>要求

**标头：** afxinet。h

##  <a name="chttpconnection"></a>CHttpConnection：： CHttpConnection

调用此成员函数来构造 `CHttpConnection` 的对象。

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>parameters

*pSession*<br/>
指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

*hConnected*<br/>
Internet 连接的句柄。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*dwContext*<br/>
`CInternetConnection` 对象的上下文标识符。 有关*dwContext*的详细信息，请参阅 "**备注**" 部分。

*nPort*<br/>
标识此连接的 Internet 端口的编号。

*pstrUserName*<br/>
指向以 null 结尾的字符串的指针，该字符串指定要登录的用户的名称。 如果为 NULL，则默认值为 anonymous。

*pstrPassword*<br/>
指向以 null 结尾的字符串的指针，该字符串指定用于登录的密码。 如果*pstrPassword*和*PSTRUSERNAME*都为 NULL，则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 null 或为空字符串，但*PSTRUSERNAME*不为 null，则使用空密码。 下表描述了*pstrUserName*和*pstrPassword*的四个可能设置的行为：

|*pstrUserName*|*pstrPassword*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或 ""|NULL 或 ""|匿名|用户的电子邮件名称|
|非空字符串|NULL 或 ""|*pstrUserName*|" "|
|Null |非空字符串|ERROR|ERROR|
|非空字符串|非空字符串|*pstrUserName*|*pstrPassword*|

dwFlags<br/>
`INTERNET_FLAG_*` 标志的任意组合。 有关*dwFlags*值的说明，请参阅[CHttpConnection：： OpenRequest](#openrequest)的 "**备注**" 部分中的表。

### <a name="remarks"></a>备注

永远不会直接创建 `CHttpConnection`。 而是通过调用[CInternetSession：： GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)来创建对象。

##  <a name="openrequest"></a>CHttpConnection：： OpenRequest

调用此成员函数以打开 HTTP 连接。

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>parameters

*pstrVerb*<br/>
指向字符串的指针，该字符串包含要在请求中使用的谓词。 如果为 NULL，则使用 "GET"。

*pstrObjectName*<br/>
指向字符串的指针，该字符串包含指定谓词的目标对象。 此字符串通常是文件名、可执行模块或搜索说明符。

*pstrReferer*<br/>
一个指向字符串的指针，该字符串指定从其获取请求中的 URL （*pstrObjectName*）的文档的地址（url）。 如果为 NULL，则未指定 HTTP 标头。

*dwContext*<br/>
`OpenRequest` 操作的上下文标识符。 有关*dwContext*的详细信息，请参阅 "备注" 部分。

*ppstrAcceptTypes*<br/>
一个指针，指向以 null 结尾的 LPCTSTR 指针数组，这些指针指向指示客户端接受的内容类型的字符串。 如果*ppstrAcceptTypes*为 NULL，则服务器将解释客户端只接受 "text/*" 类型的文档（即，只接受文本文档，而不接受图片或其他二进制文件）。 内容类型等效于 CGI 变量 CONTENT_TYPE，后者标识包含附加信息的查询（例如 HTTP POST 和 PUT）的数据类型。

*pstrVersion*<br/>
指向定义 HTTP 版本的字符串的指针。 如果为 NULL，则使用 "HTTP/1.0"。

dwFlags<br/>
INTERNET_ FLAG_ * 标志的任意组合。 有关可能的*dwFlags*值的说明，请参阅 "备注" 部分。

*nVerb*<br/>
与 HTTP 请求类型相关联的数字。 可以是以下值之一：

|HTTP 请求类型|*nVerb*值|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>返回值

指向所请求的[CHttpFile](../../mfc/reference/chttpfile-class.md)对象的指针。

### <a name="remarks"></a>备注

*dwFlags*可以是下列其中一项：

|Internet 标志|说明|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|强制从源服务器下载所请求的文件、对象或目录列表，而不是从缓存中下载。|
|INTERNET_FLAG_DONT_CACHE|不会将返回的实体添加到缓存中。|
|INTERNET_FLAG_MAKE_PERSISTENT|将返回的实体作为持久性实体添加到缓存中。 这意味着标准缓存清除、一致性检查或垃圾回收无法从缓存中删除此项。|
|INTERNET_FLAG_SECURE|使用安全事务语义。 它转换为使用 SSL/PCT，仅在 HTTP 请求中有意义|
|INTERNET_FLAG_NO_AUTO_REDIRECT|仅用于 HTTP，指定重定向不应在[CHttpFile：： SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)中自动处理。|

重写 `dwContext` 默认设置，以将上下文标识符设置为你选择的值。 上下文标识符与[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的 `CHttpConnection` 对象的特定操作相关联。 该值将返回到[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供用于标识该操作的状态。 有关上下文标识符的详细信息，请参阅文章[Internet 优先步骤： WinInet](../../mfc/wininet-basics.md) 。

此函数可能会引发异常。

## <a name="see-also"></a>另请参阅

[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
