---
title: CHttpConnection 类
ms.date: 11/04/2016
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: f7a91454b9a8619cda155f33391e5d02ae7653b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273603"
---
# <a name="chttpconnection-class"></a>CHttpConnection 类

管理与 HTTP 服务器的连接。

## <a name="syntax"></a>语法

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|创建一个 `CHttpConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|将打开一个 HTTP 请求。|

## <a name="remarks"></a>备注

HTTP 是由 MFC WinInet 类实现的三种 Internet 服务器协议之一。

该类`CHttpConnection`包含一个构造函数和一个成员函数[OpenRequest](#openrequest)，管理与 HTTP 协议与服务器的连接。

若要与 HTTP 服务器通信，必须首先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后创建[CHttpConnection](#_mfc_chttpconnection)对象。 永远不会创建`CHttpConnection`直接对象; 而是调用[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，这将创建`CHttpConnection`对象并返回的指针。

若要详细了解如何`CHttpConnection`适用于其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 Internet 协议、 gopher 和 FTP 受支持的有关连接到使用其他两个服务器的详细信息，请参见类[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)并[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection

调用此成员函数来构造`CHttpConnection`对象。

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

*pSession*<br/>
一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。

*hConnected*<br/>
Internet 连接到一个句柄。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*dwContext*<br/>
上下文标识符`CInternetConnection`对象。 请参阅**备注**有关详细信息*dwContext*。

*nPort*<br/>
标识此连接的 Internet 端口数。

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

*dwFlags*<br/>
任意组合`INTERNET_FLAG_*`标志。 请参阅中的表**备注**一部分[chttpconnection::](#openrequest)有关的说明*dwFlags*值。

### <a name="remarks"></a>备注

永远不会创建`CHttpConnection`直接。 而是通过调用创建对象[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)。

##  <a name="openrequest"></a>  CHttpConnection::OpenRequest

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

*pstrVerb*<br/>
指向一个包含要在请求中使用的谓词字符串的指针。 如果为 NULL，则使用"获取"。

*pstrObjectName*<br/>
指向包含指定的谓词的目标对象的字符串的指针。 这通常是一个文件名、 可执行模块或搜索说明符。

*pstrReferer*<br/>
指向一个字符串，指定从其文档的地址 (URL) 的请求中的 URL ( *pstrObjectName*) 获取。 如果为 NULL，指定的 HTTP 标头。

*dwContext*<br/>
上下文标识符`OpenRequest`操作。 ，请参阅备注部分的详细信息*dwContext*。

*ppstrAcceptTypes*<br/>
指向以 null 结尾 LPCTSTR 指向的指针数组，该值指示客户端接受的内容类型的字符串的指针。 如果*ppstrAcceptTypes*为 NULL，服务器解释客户端仅接受类型的文档"text / *"（即，只有文本文档并不图片或其他二进制文件）。 内容类型是等效于 CGI 变量 CONTENT_TYPE，用于标识已附加信息，如 HTTP POST 和 PUT 的查询的数据类型。

*pstrVersion*<br/>
指向定义的 HTTP 版本字符串的指针。 如果为 NULL，则使用"HTTP/1.0"。

*dwFlags*<br/>
INTERNET_ FLAG_ * 标志的任意组合。 请参阅备注部分有关的可能说明*dwFlags*值。

*nVerb*<br/>
与 HTTP 请求类型的号码。 可以是以下各项之一：

|HTTP 请求类型|*nVerb* value|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>返回值

一个指向[CHttpFile](../../mfc/reference/chttpfile-class.md)所请求对象。

### <a name="remarks"></a>备注

*dwFlags*可以是以下之一：

|Internet 标志|描述|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|源服务器中，而不是从缓存将强制下载的请求的文件、 对象或目录列表。|
|INTERNET_FLAG_DONT_CACHE|不会添加到缓存中返回的实体。|
|INTERNET_FLAG_MAKE_PERSISTENT|将返回的实体为持久实体添加到缓存。 这意味着标准缓存清理、 一致性检查，或垃圾回收无法从缓存删除该项。|
|INTERNET_FLAG_SECURE|使用安全事务语义。 这会转换为使用 SSL/百分比，才有意义的 HTTP 请求中|
|INTERNET_FLAG_NO_AUTO_REDIRECT|仅用于 HTTP，则指定的重定向操作应不会自动处理中[CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)。|

重写`dwContext`默认可为您选择的值设置的上下文标识符。 上下文标识符是否与此特定操作相关联`CHttpConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识操作的状态。 请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

与此函数可能会引发异常。

## <a name="see-also"></a>请参阅

[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
