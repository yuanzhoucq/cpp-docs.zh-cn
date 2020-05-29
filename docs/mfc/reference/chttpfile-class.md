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
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368393"
---
# <a name="chttpfile-class"></a>CHttpFile 类

提供请求和读取 HTTP 服务器上文件的功能。

## <a name="syntax"></a>语法

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CHttpFile：CHttpFile](#chttpfile)|创建一个 `CHttpFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHttpFile：：添加请求标题](#addrequestheaders)|将标头添加到发送到 HTTP 服务器的请求。|
|[CHttpFile：结束请求](#endrequest)|使用[SendRequestEx](#sendrequestex)成员功能结束发送到 HTTP 服务器的请求。|
|[CHttpFile：获取文件URL](#getfileurl)|获取指定文件的 URL。|
|[CHttpFile：获取对象](#getobject)|获取对 HTTP 服务器的请求中谓词的目标对象。|
|[CHttpFile：GetVerb](#getverb)|获取在请求到 HTTP 服务器时使用的谓词。|
|[CHttpFile：查询信息](#queryinfo)|从 HTTP 服务器返回响应或请求标头。|
|[CHttp文件：：查询信息状态代码](#queryinfostatuscode)|检索与 HTTP 请求关联的状态代码，并将其置于提供的`dwStatusCode`参数中。|
|[CHttpFile：发送请求](#sendrequest)|向 HTTP 服务器发送请求。|
|[CHttpFile：：发送请求Ex](#sendrequestex)|使用 的[写入](../../mfc/reference/cinternetfile-class.md#write)或[写入字符串](../../mfc/reference/cinternetfile-class.md#writestring)方法向 HTTP 服务器发送请求`CInternetFile`。|

## <a name="remarks"></a>备注

如果 Internet 会话从 HTTP 服务器读取数据，则必须创建 的`CHttpFile`实例。

要了解有关如何`CHttpFile`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[C互联网文件](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile：：添加请求标题

调用此成员函数以向 HTTP 请求句柄添加一个或多个 HTTP 请求标头。

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
指向包含标头或标头的字符串的指针，用于追加请求。 每个标头必须由 CR/LF 对终止。

dwFlags**<br/>
修改新标头的语义。 可以是以下值之一：

- HTTP_ADDREQ_FLAG_COALESCE合并同名的标头，使用标志将找到的第一个标头添加到后续标头。 例如，"接受：文本\*/"后跟"接受：音频/"\*导致形成单个标题"接受：文本/，\*音频/"。\* 调用应用程序由确保与使用合并或单独标头发送的请求接收的数据进行统一方案。

- HTTP_ADDREQ_FLAG_REPLACE 执行删除并添加以替换当前标头。 标头名称将用于删除当前标头，并且完整值将用于添加新标头。 如果标头值为空并且找到标头，则删除它。 如果未为空，则替换标头值。

- HTTP_ADDREQ_FLAG_ADD_IF_NEW仅添加标头（如果标头不存在）。 如果存在，则返回错误。

- HTTP_ADDREQ_FLAG_ADD与 REPLACE 一起使用。 如果标头不存在，请添加它。

*德海德伦*<br/>
*pstrHeader 的长度*（以字符表示）。 如果为 -1L，则假定*pstrHeader*为零端接，并计算长度。

*Str*<br/>
对包含要添加的请求标头或标头的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

`AddRequestHeaders`将其他自由格式标头追加到 HTTP 请求句柄。 它供需要详细控制发送到 HTTP 服务器的确切请求的先进客户端使用。

> [!NOTE]
> 应用程序可以使用HTTP_ADDREQ_FLAG_ADD或HTTP_ADDREQ_FLAG_ADD_IF_NEW在*pstrHeader 或* *str*`AddRequestHeaders`中传递多个标头。 如果应用程序尝试使用HTTP_ADDREQ_FLAG_REMOVE或HTTP_ADDREQ_FLAG_REPLACE删除或替换标头，则*lpszHeader*中只能提供一个标头。

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile：CHttpFile

调用此成员函数以构造对象`CHttpFile`。

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
互联网文件的句柄。

*h 会话*<br/>
互联网会话的句柄。

*pstrObject*<br/>
指向包含对象的字符串的`CHttpFile`指针。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*普斯特维尔布*<br/>
指向包含发送请求时要使用的方法的字符串的指针。 可以是 POST、头或 GET。

*dwContext*<br/>
`CHttpFile`对象的上下文标识符。 有关此参数的详细信息，请参阅**备注**。

*p连接*<br/>
指向[CHttpConnect](../../mfc/reference/chttpconnection-class.md)对象的指针。

### <a name="remarks"></a>备注

您从不直接构造`CHttpFile`对象;而是调用[CInternetSession：：打开URL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnect：打开请求](../../mfc/reference/chttpconnection-class.md#openrequest)。

MFC 的`dwContext`默认值由 MFC 从`CHttpFile`创建`CHttpFile`对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象发送到对象。 调用`CInternetSession::OpenURL`或`CHttpConnection`构造对象时`CHttpFile`，可以重写默认值，将上下文标识符设置为您选择的值。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile：结束请求

调用此成员函数以结束使用[SendRequestEx](#sendrequestex)成员函数发送到 HTTP 服务器的请求。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
描述操作的标志。 有关相应标志的列表，请参阅 Windows SDK 中的[HttpEndRequest。](/windows/win32/api/wininet/nf-wininet-httpendrequestw)

*lpBuffin*<br/>
指向初始[化INTERNET_BUFFERS，](/windows/win32/api/wininet/ns-wininet-internet_buffersw)用于描述用于操作的输入缓冲区。

*dwContext*<br/>
操作的`CHttpFile`上下文标识符。 有关此参数的详细信息，请参阅备注。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

mFC 从`CHttpFile`创建对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md) `CHttpFile`对象向对象发送*dwContext*的默认值。 当您调用[CInternetSession：：OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnect](../../mfc/reference/chttpconnection-class.md) `CHttpFile`构造对象时，可以重写默认值，将上下文标识符设置为您选择的值。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅文章"Internet 第一步：WinInet"。](../../mfc/wininet-basics.md)

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile：获取文件URL

调用此成员函数以获取 HTTP 文件的名称作为 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

包含引用与此文件关联的资源的 URL 的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

### <a name="remarks"></a>备注

仅当成功调用[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象上时，才使用此成员函数。

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile：获取对象

调用此成员函数以获取与此关联的对象的名称`CHttpFile`。

```
CString GetObject() const;
```

### <a name="return-value"></a>返回值

包含对象名称的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

### <a name="remarks"></a>备注

仅当成功调用[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象上时，才使用此成员函数。

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile：GetVerb

调用此成员函数以获取与此关联的 HTTP 谓词（或方法`CHttpFile`）。

```
CString GetVerb() const;
```

### <a name="return-value"></a>返回值

包含 HTTP 谓词（或方法）名称的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

### <a name="remarks"></a>备注

仅当成功调用[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象上时，才使用此成员函数。

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile：查询信息

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
要查询的属性和指定请求的信息类型的以下标志的组合：

- HTTP_QUERY_CUSTOM 查找标头名称并在输出时在*lpvBuffer*中返回此值。 如果未找到标头，HTTP_QUERY_CUSTOM引发断言。

- HTTP_QUERY_FLAG_REQUEST_HEADERS通常，应用程序查询响应标头，但应用程序也可以使用此标志查询请求标头。

- HTTP_QUERY_FLAG_SYSTEMTIME对于值为日期/时间字符串（如"上次修改时间"）的标头，此标志将标头值作为标准 Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构返回，该结构不需要应用程序来分析数据。 如果使用此标志，则可能需要使用函数的`SYSTEMTIME`重写。

- HTTP_QUERY_FLAG_NUMBER 对于值为数字的标头（如状态代码），此标志将数据作为 32 位数字返回。

有关可能值的列表，请参阅**备注**部分。

*lpvBuffer*<br/>
指向接收信息的缓冲区的指针。

*lpdwBuffer 长度*<br/>
在输入时，这将指向包含数据缓冲区长度（以字符数或字节数）的值。 有关此参数的详细信息，请参阅**备注**部分。

*lpdwIndex*<br/>
指向零基标头索引的指针。 可以为 NULL。 使用此标志可以枚举具有相同名称的多个标头。 在输入时 *，lpdwIndex*指示要返回的指定标头的索引。 在输出时 *，lpdwIndex*指示下一个标头的索引。 如果找不到下一个索引，则返回ERROR_HTTP_HEADER_NOT_FOUND。

*Str*<br/>
对接收返回信息的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

*dwIndex*<br/>
索引值。 请参阅*lpdwIndex*。

*pSysTime*<br/>
指向 Win32[系统时间结构的](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

仅当成功调用[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象上时，才使用此成员函数。

可以从 中检索以下类型的数据`QueryInfo`：

- 字符串（默认）

- `SYSTEMTIME`（对于"数据"："过期"等，标题）

- DWORD（用于STATUS_CODE、CONTENT_LENGTH等）

当字符串写入缓冲区并且成员函数成功时，`lpdwBufferLength`字符串的长度为字符减去 1 表示终止 NULL 字符。

可能的*dwInfoLevel*值包括：

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

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttp文件：：查询信息状态代码

调用此成员函数获取与 HTTP 请求关联的状态代码，并将其放置在提供的*dwStatusCode*参数中。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>参数

*dwStatusCode*<br/>
对状态代码的引用。 状态代码指示请求事件的成功或失败。 有关状态代码说明的选择，请参阅**备注**。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

仅当成功调用[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功创建的对象上时，才使用此成员函数。

HTTP 状态代码分为指示请求成功或失败的组。 下表概述了状态代码组和最常见的 HTTP 状态代码。

|组|含义|
|-----------|-------------|
|200-299|Success|
|300-399|信息|
|400-499|请求错误|
|500-599|服务器错误|

常见 HTTP 状态代码：

|状态代码|含义|
|-----------------|-------------|
|200|找到了 URL，接下来进行传输|
|400|无法理解的请求|
|404|找不到请求的 URL|
|405|服务器不支持请求的方法|
|500|未知的服务器错误|
|503|已达到服务器容量|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile：发送请求

调用此成员函数以向 HTTP 服务器发送请求。

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
指向包含要发送的标头名称的字符串的指针。

*德海德伦*<br/>
由*pstrHeader*标识的标头的长度。

*lp 可选*<br/>
在请求标头之后立即发送的任何可选数据。 这通常用于 POST 和 PUT 操作。 如果没有要发送的可选数据，则这可以为 NULL。

*德沃纳伦*<br/>
*lp 可选*的长度。

*串标题*<br/>
包含要发送的请求的标头名称的字符串。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile：：发送请求Ex

调用此成员函数以向 HTTP 服务器发送请求。

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

*德·道伦*<br/>
要在请求中发送的字节数。

dwFlags**<br/>
描述操作的标志。 有关适当的标志列表，请参阅 Windows SDK 中的[HttpSendRequestEx。](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw)

*dwContext*<br/>
操作的`CHttpFile`上下文标识符。 有关此参数的详细信息，请参阅备注。

*lpBuffin*<br/>
指向初始[化INTERNET_BUFFERS，](/windows/win32/api/wininet/ns-wininet-internet_buffersw)用于描述用于操作的输入缓冲区。

*lpBuffOut*<br/>
指向初始化INTERNET_BUFFERS的指针，该INTERNET_BUFFERS描述用于操作的输出缓冲区。

### <a name="return-value"></a>返回值

如果成功，则为非零。 如果调用失败，请通过检查引发的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象来确定失败的原因。

### <a name="remarks"></a>备注

此函数允许应用程序使用`CInternetFile`的[写入](../../mfc/reference/cinternetfile-class.md#write)和[写入String](../../mfc/reference/cinternetfile-class.md#writestring)方法发送数据。 在调用此函数的任一重写之前，必须知道要发送的数据的长度。 第一个覆盖允许您指定要发送的数据长度。 第二个重写接受指向INTERNET_BUFFERS结构的指针，这些结构可用于详细描述缓冲区。

将内容写入文件后，调用[EndRequest](#endrequest)以结束操作。

mFC 从`CHttpFile`创建对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md) `CHttpFile`对象向对象发送*dwContext*的默认值。 当您调用[CInternetSession：：OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnect](../../mfc/reference/chttpconnection-class.md) `CHttpFile`构造对象时，可以重写默认值，将上下文标识符设置为您选择的值。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

### <a name="example"></a>示例

此代码片段将字符串的内容发送到名为 MFCISAPI 的 DLL。本地主机上的 DLL。 此示例仅对 使用 一个`WriteString`调用，使用多个调用以块发送数据是可以接受的。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttp连接类](../../mfc/reference/chttpconnection-class.md)
