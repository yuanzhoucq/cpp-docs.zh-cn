---
title: "CHttpFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e9af23bb74ba8e96f29a5b7cc4139d2932df8c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chttpfile-class"></a>CHttpFile 类
提供请求和读取 HTTP 服务器上文件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHttpFile::CHttpFile](#chttpfile)|创建一个 `CHttpFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|将标头添加到与 HTTP 服务器发送的请求。|  
|[CHttpFile::EndRequest](#endrequest)|结束请求发送到的 HTTP 服务器与[SendRequestEx](#sendrequestex)成员函数。|  
|[CHttpFile::GetFileURL](#getfileurl)|对指定文件中获取的 URL。|  
|[CHttpFile::GetObject](#getobject)|与 HTTP 服务器在请求中获取该谓词的目标对象。|  
|[CHttpFile::GetVerb](#getverb)|获取与 HTTP 服务器的请求中使用的谓词。|  
|[CHttpFile::QueryInfo](#queryinfo)|从 HTTP 服务器返回响应或请求标头。|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|检索与 HTTP 请求关联的状态代码并将其放在所提供`dwStatusCode`参数。|  
|[CHttpFile::SendRequest](#sendrequest)|与 HTTP 服务器发送请求。|  
|[CHttpFile::SendRequestEx](#sendrequestex)|将请求发送到 HTTP 服务器使用[编写](../../mfc/reference/cinternetfile-class.md#write)或[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。|  
  
## <a name="remarks"></a>备注  
 如果 Internet 会话读取 HTTP 服务器中的数据，则必须创建的实例`CHttpFile`。  
  
 若要了解有关如何`CHttpFile`工作与其他 MFC Internet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxinet.h  
  
##  <a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders  
 调用此成员函数添加一个或多个新的 HTTP 请求标头可对 HTTP 请求处理。  
  
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
 `pstrHeaders`  
 指向包含标头或标头，以便将附加到请求的字符串的指针。 必须由 CR/LF 对终止每个标头。  
  
 `dwFlags`  
 修改新的头文件的语义。 可以是以下各项之一：  
  
- `HTTP_ADDREQ_FLAG_COALESCE`将合并具有相同的名称，使用标志添加到后续的标头中找到的第一个标头的标头。 例如，"接受： 文本 / *"后跟"接受： 音频 /\*"结果中的单个标头形成"接受： 文本 /\*、 音频 /\*"。 它是由调用应用程序中，以确保与已接收数据的请求都发送合并或单独标头凝聚力方案。  
  
- `HTTP_ADDREQ_FLAG_REPLACE`执行删除并添加要替换当前标头。 标头名称将用于删除当前的标头，而将使用完整的值来添加新的标头。 如果标头值为空并且找到标头，则会删除。 如果不为空，则将替换标头值。  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW`如果不存在，请仅添加标头。 如果存在，则返回错误。  
  
- `HTTP_ADDREQ_FLAG_ADD`用于替换。 如果不存在，请添加标头。  
  
 `dwHeadersLen`  
 长度，以字符为单位的`pstrHeaders`。 如果这是-1l，然后`pstrHeaders`被假定为零终止和计算长度。  
  
 `str`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含请求标头或标头要添加的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `AddRequestHeaders`将其他，自由格式的标头追加到 HTTP 请求句柄。 它被旨在使用由复杂的客户端都需要对发送到 HTTP 服务器的确切请求的详细的控制。  
  
> [!NOTE]
>  应用程序可以将多个标头中的传递`pstrHeaders`或`str`为`AddRequestHeaders`调用使用`HTTP_ADDREQ_FLAG_ADD`或`HTTP_ADDREQ_FLAG_ADD_IF_NEW`。 如果应用程序将尝试删除或替换标头使用**HTTP_ADDREQ_FLAG_REMOVE**或`HTTP_ADDREQ_FLAG_REPLACE`，只有一个标头可以提供在`lpszHeaders`。  
  
##  <a name="chttpfile"></a>CHttpFile::CHttpFile  
 此成员函数调用以构造`CHttpFile`对象。  
  
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
 `hFile`  
 Internet 文件的句柄。  
  
 `hSession`  
 Internet 会话句柄。  
  
 *pstrObject*  
 指向一个字符串，包含`CHttpFile`对象。  
  
 `pstrServer`  
 指向包含的服务器名称的字符串的指针。  
  
 `pstrVerb`  
 指向包含要发送请求时使用的方法的字符串的指针。 可以是**POST**，**头**，或`GET`。  
  
 dwContext  
 上下文标识符`CHttpFile`对象。 请参阅**备注**有关此参数的详细信息。  
  
 `pConnection`  
 指向的指针[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象。  
  
### <a name="remarks"></a>备注  
 永远不会构造`CHttpFile`直接对象; 而是调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)相反。  
  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当调用`CInternetSession::OpenURL`或`CHttpConnection`构造`CHttpFile`对象，您可以重写默认设置，以便为你选择的值设置的上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="endrequest"></a>CHttpFile::EndRequest  
 调用此成员函数以结束与 HTTP 服务器与发送的请求[SendRequestEx](#sendrequestex)成员函数。  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 描述该操作的标志。 有关相应标志的列表，请参阅[HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) Windows SDK 中。  
  
 `lpBuffIn`  
 指向已初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用于该操作的输入的缓冲区。  
  
 `dwContext`  
 上下文标识符`CHttpFile`操作。 有关此参数的详细信息，请参阅备注。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)构造`CHttpFile`对象，您可以重写默认设置，以便为你选择的值设置的上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="getfileurl"></a>CHttpFile::GetFileURL  
 调用此成员函数可获取作为 URL 的 HTTP 文件的名称。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含引用与此文件关联的资源的 URL。  
  
### <a name="remarks"></a>备注  
 只有在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="getobject"></a>CHttpFile::GetObject  
 调用此成员函数可获取与此关联的对象的名称`CHttpFile`。  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含对象的名称。  
  
### <a name="remarks"></a>备注  
 只有在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="getverb"></a>CHttpFile::GetVerb  
 调用此成员函数可获取与此关联的 HTTP 谓词 （或方法） `CHttpFile`。  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含的 HTTP 谓词 （或方法） 的名称。  
  
### <a name="remarks"></a>备注  
 只有在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="queryinfo"></a>CHttpFile::QueryInfo  
 调用此成员函数以返回响应或请求通过 HTTP 请求标头。  
  
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
 `dwInfoLevel`  
 特性查询和指定的请求信息的类型的以下标志的组合：  
  
- **HTTP_QUERY_CUSTOM**查找标头名称并返回中的此值`lpvBuffer`输出。 **HTTP_QUERY_CUSTOM**引发断言，如果没有找到标头。  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS**通常，应用程序查询响应标头，但应用程序还可以使用此标志查询请求标头。  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME**对于这些标头，其值为日期/时间字符串，如"上次修改时间，"此标志返回的标头值与标准 Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)不需要的结构若要分析的数据的应用程序。 如果你使用此标志，你可能想要使用`SYSTEMTIME`重写的函数。  
  
- **HTTP_QUERY_FLAG_NUMBER**此标志将数据作为 32 位数字返回有关其值是一个数字，例如状态代码，这些标头。  
  
 请参阅**备注**有关列表的可能值的部分。  
  
 `lpvBuffer`  
 指向接收信息的缓冲区的指针。  
  
 `lpdwBufferLength`  
 在进入时，这指向包含数据缓冲区中的字符数或字节的长度的值。 请参阅**备注**部分更多详细信息，有关此参数。  
  
 `lpdwIndex`  
 指向从零开始的标头索引的指针。 可以是**NULL**。 使用此标志枚举具有相同名称的多个标头。 在输入时，`lpdwIndex`指示指定的标头返回的索引。 在输出时，`lpdwIndex`指示下一步的标头的索引。 如果找不到下一步的索引， **ERROR_HTTP_HEADER_NOT_FOUND**返回。  
  
 `str`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收返回的信息的对象。  
  
 `dwIndex`  
 一个索引值。 请参阅 `lpdwIndex`。  
  
 *pSysTime*  
 一个指向 Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 只有在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 你可以检索以下类型的数据从`QueryInfo`:  
  
-   字符串 （默认值）  
  
- `SYSTEMTIME`(对于"数据:""Expires:"等等，标头)  
  
- `DWORD`(有关**STATUS_CODE**， **CONTENT_LENGTH**等。)  
  
 当字符串写入缓冲区，并且成员函数成功，`lpdwBufferLength`包含以字符为单位减 1 的终止的字符串的长度**NULL**字符。  
  
 可能`dwInfoLevel`值包括：  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode  
 调用此成员函数可获取 HTTP 请求与关联的状态代码并将其置于提供`dwStatusCode`参数。  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwStatusCode`  
 对状态代码的引用。 状态代码指示成功或失败的请求的事件。 请参阅**备注**针对选择的状态代码说明。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 只有在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 HTTP 状态代码划分为组，该值指示是成功还是失败的请求。 下表概述了状态代码组和最常见的 HTTP 状态代码。  
  
|Group|含义|  
|-----------|-------------|  
|200-299|成功|  
|300-399|信息|  
|400-499|请求错误|  
|500-599|服务器错误|  
  
 常见的 HTTP 状态代码：  
  
|状态代码|含义|  
|-----------------|-------------|  
|200|找到了 URL，接下来进行传输|  
|400|无法理解的请求|  
|404|找不到请求的 URL|  
|405|服务器不支持请求的方法|  
|500|未知的服务器错误|  
|503|已达到服务器容量|  
  
##  <a name="sendrequest"></a>CHttpFile::SendRequest  
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
 `pstrHeaders`  
 指向包含要发送的标头的名称的字符串的指针。  
  
 `dwHeadersLen`  
 由标识标头的长度`pstrHeaders`。  
  
 `lpOptional`  
 要发送的请求标头后立即任何可选数据。 这通常适用于**POST**和**放**操作。 这可以是**NULL**如果没有要发送的可选数据。  
  
 *dwOptionalLen*  
 `lpOptional` 的长度。  
  
 `strHeaders`  
 包含正在发送的请求标头的名称的字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx  
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
 *dwTotalLen*  
 要在请求中发送的字节数。  
  
 `dwFlags`  
 描述该操作的标志。 有关相应标志的列表，请参阅[HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) Windows SDK 中。  
  
 `dwContext`  
 上下文标识符`CHttpFile`操作。 有关此参数的详细信息，请参阅备注。  
  
 `lpBuffIn`  
 指向已初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用于该操作的输入的缓冲区。  
  
 *lpBuffOut*  
 指向已初始化**INTERNET_BUFFERS**描述用于该操作的输出缓冲区。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为非 0。 如果调用失败，则通过检查引发确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此函数允许你的应用程序将使用的数据发送[编写](../../mfc/reference/cinternetfile-class.md#write)和[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。 你必须知道要在调用此函数的任一重写之前发送的数据的长度。 第一个替代，可指定你想要发送的数据的长度。 第二个替代接受指向**INTERNET_BUFFERS**结构，可用于描述十分详尽地缓冲区。  
  
 内容写入到文件后，调用[EndRequest](#endrequest)来取消操作。  
  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)构造`CHttpFile`对象，您可以重写默认设置，以便为你选择的值设置的上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
### <a name="example"></a>示例  
 此代码段将字符串的内容发送到名为 MFCISAPI DLL。本地主机服务器上的 DLL。 此示例使用仅一次调用时`WriteString`，使用多个调用将数据发送在块中是可以接受。  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)
