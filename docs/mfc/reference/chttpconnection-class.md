---
title: CHttp连接类
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
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351814"
---
# <a name="chttpconnection-class"></a>CHttp连接类

管理与 HTTP 服务器的连接。

## <a name="syntax"></a>语法

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHttp连接：：CHttp连接](#chttpconnection)|创建一个 `CHttpConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|打开 HTTP 请求。|

## <a name="remarks"></a>备注

HTTP 是 MFC WinInet 类实现的三个 Internet 服务器协议之一。

该类`CHttpConnection`包含一个构造函数和一个成员函数[OpenRequest](#openrequest)，用于管理与具有 HTTP 协议的服务器的连接。

要与 HTTP 服务器通信，必须首先创建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的实例，然后创建[CHttpConnect](#chttpconnection)对象。 您从不直接创建`CHttpConnection`对象;相反，调用[CInternetSession：：GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，它`CHttpConnection`创建对象并返回指向它的指针。

要了解有关如何`CHttpConnection`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。 有关使用其他两个受支持的 Internet 协议（gopher 和 FTP）连接到服务器的详细信息，请参阅[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)的类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 互联网连接](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttp连接：：CHttp连接

调用此成员函数以构造对象`CHttpConnection`。

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

### <a name="parameters"></a>参数

*p 会话*<br/>
指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

*h 连接*<br/>
互联网连接的句柄。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*dwContext*<br/>
`CInternetConnection`对象的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**部分。

*n波特*<br/>
标识此连接的 Internet 端口的数字。

*pstrUser 名称*<br/>
指向 null 终止字符串的指针，该字符串指定要登录的用户的名称。 如果为 NULL，则默认值为匿名。

*pstr密码*<br/>
指向 null 终止字符串的指针，用于指定用于登录的密码。 如果*pstrPassword*和*pstrUserName*均为 NULL，则默认的匿名密码是用户的电子邮件名称。 如果*pstrPassword*为 NULL 或空字符串，但*pstrUserName*不是 NULL，则使用空白密码。 下表描述了*pstrUserName*和*pstrPassword*的四种可能设置的行为：

|*pstrUser 名称*|*pstr密码*|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|用户的电子邮件名称|
|非 NULL 字符串|NULL 或""|*pstrUser 名称*|" "|
|Null |非 NULL 字符串|ERROR|ERROR|
|非 NULL 字符串|非 NULL 字符串|*pstrUser 名称*|*pstr密码*|

dwFlags**<br/>
标志的`INTERNET_FLAG_*`任意组合。 请参阅[CHttpConnection：：打开请求的备](#openrequest)**注**部分中的表，了解*dwFlags*值的说明。

### <a name="remarks"></a>备注

您从不直接创建`CHttpConnection`。 相反，您可以通过调用[CInternetSession：：getHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)来创建对象。

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttp连接：：打开请求

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

### <a name="parameters"></a>参数

*普斯特维尔布*<br/>
指向包含要在请求中使用的谓词的字符串的指针。 如果为 NULL，则使用"GET"。

*pstrObject名称*<br/>
指向包含指定谓词的目标对象的字符串的指针。 此字符串通常是文件名、可执行模块或搜索指定器。

*普斯特克弗*<br/>
指向字符串的指针，用于指定从中获取*请求中的*URL 的文档的地址 （URL） 的指针。 如果 NULL，则未指定 HTTP 标头。

*dwContext*<br/>
操作的`OpenRequest`上下文标识符。 有关*dwContext*的详细信息，请参阅备注部分。

*ppstr 接受类型*<br/>
指向 LPCTSTR 的 null 端结束的数组的指针指向指示客户端接受的内容类型的字符串。 如果*ppstrAcceptType*为 NULL，则服务器将解释客户端仅接受类型为"文本/*"的文档（即，仅接受文本文档，而不是图片或其他二进制文件）。 内容类型等效于 CGI 变量CONTENT_TYPE，该变量标识具有附加信息的查询（如 HTTP POST 和 PUT）的数据类型。

*普斯特里斯特*<br/>
指向定义 HTTP 版本的字符串的指针。 如果为 NULL，则使用"HTTP/1.0"。

dwFlags**<br/>
INTERNET_FLAG_* 标志的任意组合。 有关可能的*dwFlags*值的说明，请参阅备注部分。

*nVerb*<br/>
与 HTTP 请求类型关联的数字。 可以是以下值之一：

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

请求的指向[CHttpFile](../../mfc/reference/chttpfile-class.md)对象的指针。

### <a name="remarks"></a>备注

*dwFlags*可以是以下原因之一：

|互联网标志|说明|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|强制从源服务器而不是从缓存下载请求的文件、对象或目录列表。|
|INTERNET_FLAG_DONT_CACHE|不会将返回的实体添加到缓存中。|
|INTERNET_FLAG_MAKE_PERSISTENT|将返回的实体作为持久实体添加到缓存中。 这意味着标准缓存清理、一致性检查或垃圾回收无法从缓存中删除此项。|
|INTERNET_FLAG_SECURE|使用安全事务语义。 它转换为使用 SSL/PCT，仅在 HTTP 请求中有意义|
|INTERNET_FLAG_NO_AUTO_REDIRECT|仅与 HTTP 一起使用，指定不应在[CHttpFile 中自动处理重定向：：发送请求](../../mfc/reference/chttpfile-class.md#sendrequest)。|

覆盖`dwContext`默认值，将上下文标识符设置为您选择的值。 上下文标识符与其`CHttpConnection`[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建的对象的此特定操作相关联。 该值将返回到[CInternetSession：：onStatusBack，](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供标识该值的操作的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

此函数可能会引发异常。

## <a name="see-also"></a>另请参阅

[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
