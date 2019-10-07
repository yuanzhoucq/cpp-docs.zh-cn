---
title: CHttpFile 类
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: 0c8c401b43361a5e1472e3470f5ea452c91b957f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505965"
---
# <a name="chttpfile-class"></a>CHttpFile 类

提供请求和读取 HTTP 服务器上文件的功能。

## <a name="syntax"></a>语法

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CHttpFile:: CHttpFile](#chttpfile)|创建一个 `CHttpFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|向发送到 HTTP 服务器的请求添加标头。|
|[CHttpFile::EndRequest](#endrequest)|结束使用[SendRequestEx](#sendrequestex)成员函数发送到 HTTP 服务器的请求。|
|[CHttpFile::GetFileURL](#getfileurl)|获取指定文件的 URL。|
|[CHttpFile::GetObject](#getobject)|获取对 HTTP 服务器的请求中谓词的目标对象。|
|[CHttpFile::GetVerb](#getverb)|获取在向 HTTP 服务器发出的请求中使用的谓词。|
|[CHttpFile::QueryInfo](#queryinfo)|返回 HTTP 服务器的响应或请求标头。|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|检索与某个 HTTP 请求关联的状态代码, 并将其放在`dwStatusCode`所提供的参数中。|
|[CHttpFile::SendRequest](#sendrequest)|向 HTTP 服务器发送请求。|
|[CHttpFile::SendRequestEx](#sendrequestex)|使用的[Write](../../mfc/reference/cinternetfile-class.md#write)或[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`将请求发送到 HTTP 服务器。|

## <a name="remarks"></a>备注

如果 Internet 会话读取 HTTP 服务器中的数据, 则必须创建的`CHttpFile`实例。

若要了解有关如何`CHttpFile`使用其他 MFC Internet 类的详细信息, 请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>要求

**标头:** afxinet。h

##  <a name="addrequestheaders"></a>CHttpFile:: AddRequestHeaders

调用此成员函数可将一个或多个 HTTP 请求标头添加到 HTTP 请求句柄。

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>参数

*pstrHeaders*<br/>
指向字符串的指针, 该字符串包含要追加到请求中的标头或标头。 每个标头必须以 CR/LF 对结尾。

*dwFlags*<br/>
修改新标头的语义。 可以是以下各项之一：

- HTTP_ADDREQ_FLAG_COALESCE 合并同名的标头, 并使用标志来添加找到的第一个标头。 例如, "accept\*: text/" 后跟 "accept: audio/\*" 会生成单个标头 "accept: text/\*, audio/\*"。 这取决于调用应用程序, 以确保与通过合并或单独标头发送的请求所收到的数据有关的统一方案。

- HTTP_ADDREQ_FLAG_REPLACE 执行删除并添加来替换当前标头。 标头名称将用于删除当前标头, 而完整值将用于添加新标头。 如果标头值为空并且找到了标头, 则将其删除。 如果不为空, 则替换标头值。

- HTTP_ADDREQ_FLAG_ADD_IF_NEW 仅添加标头 (如果尚未存在)。 如果存在错误, 则返回一个错误。

- 与 REPLACE 一起使用的 HTTP_ADDREQ_FLAG_ADD。 如果标头不存在, 则添加标头。

*dwHeadersLen*<br/>
*PstrHeaders*的长度, 以字符为字符。 如果这是-1L, 则假定*pstrHeaders*为零终止, 并计算长度。

*str*<br/>
对包含要添加的请求标头或标头的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

`AddRequestHeaders`向 HTTP 请求句柄追加额外的自由格式标头。 它旨在供需要详细控制发送到 HTTP 服务器的准确请求的复杂客户端使用。

> [!NOTE]
>  应用程序可以使用 HTTP_ADDREQ_FLAG_ADD 或 HTTP_ADDREQ_FLAG_ADD_IF_NEW, 将 `AddRequestHeaders`多个标头传递到*pstrHeaders*或 str 中的多个标头。 如果应用程序尝试使用 HTTP_ADDREQ_FLAG_REMOVE 或 HTTP_ADDREQ_FLAG_REPLACE 删除或替换标头, 则*lpszHeaders*中只能提供一个标头。

##  <a name="chttpfile"></a>CHttpFile:: CHttpFile

调用此成员函数来构造`CHttpFile`对象。

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>参数

*hFile*<br/>
Internet 文件的句柄。

*hSession*<br/>
Internet 会话的句柄。

*pstrObject*<br/>
指向包含`CHttpFile`对象的字符串的指针。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*pstrVerb*<br/>
指向字符串的指针, 该字符串包含要在发送请求时使用的方法。 可以是 POST、HEAD 或 GET。

*dwContext*<br/>
`CHttpFile`对象的上下文标识符。 有关此参数的详细信息, 请参阅**备注**。

*pConnection*<br/>
指向[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象的指针。

### <a name="remarks"></a>备注

永远不会直接`CHttpFile`构造对象, 而应改为调用[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) 。

MFC 将的默认`dwContext`值从创建`CHttpFile`对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象发送`CHttpFile`到对象。 当你调用`CInternetSession::OpenURL`或`CHttpConnection`来构造`CHttpFile`对象时, 你可以重写默认值, 以将上下文标识符设置为你选择的值。 上下文标识符返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在标识它的对象上提供状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

##  <a name="endrequest"></a>CHttpFile:: EndRequest

使用[SendRequestEx](#sendrequestex)成员函数调用此成员函数以结束发送到 HTTP 服务器的请求。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
描述操作的标志。 有关适当标志的列表, 请参阅 Windows SDK 中的[HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) 。

*lpBuffIn*<br/>
一个指针, 指向用于描述用于操作的输入缓冲区的已初始化[INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) 。

*dwContext*<br/>
`CHttpFile`操作的上下文标识符。 有关此参数的详细信息, 请参阅备注。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

*DwContext*的默认值由 MFC 发送到创建该`CHttpFile` `CHttpFile`对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象中的对象。 调用[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile`来构造对象时, 可以重写默认值, 将上下文标识符设置为所选的值。 上下文标识符返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在标识它的对象上提供状态。 请参阅[文章 Internet 优先步骤:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

##  <a name="getfileurl"></a>CHttpFile:: GetFileURL

调用此成员函数以获取作为 URL 的 HTTP 文件的名称。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象, 其中包含一个引用与此文件关联的资源的 URL。

### <a name="remarks"></a>备注

只有在成功调用[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象之后, 才能使用此成员函数。

##  <a name="getobject"></a>  CHttpFile::GetObject

调用此成员函数可获取与此`CHttpFile`关联的对象的名称。

```
CString GetObject() const;
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象, 其中包含对象的名称。

### <a name="remarks"></a>备注

只有在成功调用[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象之后, 才能使用此成员函数。

##  <a name="getverb"></a>  CHttpFile::GetVerb

调用此成员函数可获取与此`CHttpFile`关联的 HTTP 谓词 (或方法)。

```
CString GetVerb() const;
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象, 其中包含 HTTP 谓词 (或方法) 的名称。

### <a name="remarks"></a>备注

只有在成功调用[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象之后, 才能使用此成员函数。

##  <a name="queryinfo"></a>CHttpFile:: QueryInfo

调用此成员函数以从 HTTP 请求返回响应或请求标头。

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>参数

*dwInfoLevel*<br/>
要查询的属性和指定所请求的信息类型的下列标志的组合:

- HTTP_QUERY_CUSTOM 查找标头名称, 并在输出中的*lpvBuffer*中返回此值。 如果找不到标头, HTTP_QUERY_CUSTOM 将引发断言。

- HTTP_QUERY_FLAG_REQUEST_HEADERS 通常情况下, 应用程序会查询响应标头, 但应用程序也可以使用此标志来查询请求标头。

- HTTP_QUERY_FLAG_SYSTEMTIME 对于其值为日期/时间字符串的标头 (如 "上次修改时间"), 此标志将标头值作为标准 Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构返回, 而不需要应用程序对数据进行分析。 如果使用此标志, 则可能需要使用`SYSTEMTIME`函数的重写。

- HTTP_QUERY_FLAG_NUMBER 对于值为数字的标头 (如状态代码), 此标志以32位数字的形式返回数据。

有关可能值的列表, 请参阅 "**备注**" 部分。

*lpvBuffer*<br/>
指向接收信息的缓冲区的指针。

*lpdwBufferLength*<br/>
输入时, 这将指向一个值, 该值包含数据缓冲区的长度 (以字符数或字节数表示)。 有关此参数的详细信息, 请参阅 "**备注**" 部分。

*lpdwIndex*<br/>
指向从零开始的标头索引的指针。 可以为 NULL。 使用此标志可枚举多个具有相同名称的标头。 对于 input, *lpdwIndex*指示要返回的指定标头的索引。 在输出时, *lpdwIndex*指示下一标头的索引。 如果找不到下一个索引, 则返回 ERROR_HTTP_HEADER_NOT_FOUND。

*str*<br/>
对接收返回信息的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

*dwIndex*<br/>
索引值。 请参阅*lpdwIndex*。

*pSysTime*<br/>
指向 Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

只有在成功调用[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象之后, 才能使用此成员函数。

可以从以下类型的数据中`QueryInfo`检索以下类型的数据:

- 字符串 (默认值)

- `SYSTEMTIME`(对于 "数据:" "过期:" 等)

- DWORD (适用于 STATUS_CODE、CONTENT_LENGTH 等)

将字符串写入缓冲区后, 如果成员函数成功, 则包含以字符`lpdwBufferLength`结尾的字符串长度 (对于终止 NULL 字符)。

可能的*dwInfoLevel*值包括:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

##  <a name="queryinfostatuscode"></a>CHttpFile:: QueryInfoStatusCode

调用此成员函数以获取与某个 HTTP 请求关联的状态代码, 并将其放入提供的*dwStatusCode*参数。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>参数

*dwStatusCode*<br/>
对状态代码的引用。 状态代码指示请求的事件是成功还是失败。 有关状态代码说明的选择, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

只有在成功调用[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象之后, 才能使用此成员函数。

HTTP 状态代码分为组, 指出请求是成功还是失败。 下表概述了状态代码组和最常见的 HTTP 状态代码。

|Group|含义|
|-----------|-------------|
|200-299|Success|
|300-399|Information|
|400-499|请求错误|
|500-599|服务器错误|

常见的 HTTP 状态代码:

|状态代码|含义|
|-----------------|-------------|
|200|找到了 URL，接下来进行传输|
|400|无法理解的请求|
|404|找不到请求的 URL|
|405|服务器不支持请求的方法|
|500|未知的服务器错误|
|503|已达到服务器容量|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

调用此成员函数以将请求发送到 HTTP 服务器。

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>参数

*pstrHeaders*<br/>
指向字符串的指针, 该字符串包含要发送的标头的名称。

*dwHeadersLen*<br/>
由*pstrHeaders*标识的标头的长度。

*lpOptional*<br/>
要在请求标头之后立即发送的任何可选数据。 这通常用于 POST 和 PUT 操作。 如果没有要发送的可选数据, 则此值可以为 NULL。

*dwOptionalLen*<br/>
*LpOptional*的长度。

*strHeaders*<br/>
一个字符串, 其中包含要发送的请求的标头的名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

##  <a name="sendrequestex"></a>CHttpFile:: SendRequestEx

调用此成员函数以将请求发送到 HTTP 服务器。

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*dwTotalLen*<br/>
要在请求中发送的字节数。

*dwFlags*<br/>
描述操作的标志。 有关适当标志的列表, 请参阅 Windows SDK 中的[HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) 。

*dwContext*<br/>
`CHttpFile`操作的上下文标识符。 有关此参数的详细信息, 请参阅备注。

*lpBuffIn*<br/>
一个指针, 指向用于描述用于操作的输入缓冲区的已初始化[INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) 。

*lpBuffOut*<br/>
一个指针, 指向用于描述用于操作的输出缓冲区的已初始化 INTERNET_BUFFERS。

### <a name="return-value"></a>返回值

如果成功, 则为非零值。 如果调用失败, 则通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

此函数允许你的应用程序使用的[Write](../../mfc/reference/cinternetfile-class.md#write)和[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`发送数据。 在调用此函数的任何重写之前, 必须知道要发送的数据的长度。 第一次替代允许您指定要发送的数据的长度。 第二次重写接受指向 INTERNET_BUFFERS 结构的指针, 这些结构可用于更详细地描述缓冲区。

将内容写入文件后, 调用[EndRequest](#endrequest)结束操作。

*DwContext*的默认值由 MFC 发送到创建该`CHttpFile` `CHttpFile`对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象中的对象。 调用[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile`来构造对象时, 可以重写默认值, 将上下文标识符设置为所选的值。 上下文标识符返回到[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在标识它的对象上提供状态。 请参阅 Internet [First 步骤一文:WinInet](../../mfc/wininet-basics.md) , 详细了解上下文标识符。

### <a name="example"></a>示例

此代码段将字符串的内容发送到名为 MFCISAPI 的 DLL。DLL。 虽然此示例只使用一次调用`WriteString`, 但使用多个调用来发送块中的数据是可接受的。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>请参阅

[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)
