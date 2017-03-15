---
title: "CHttpFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpFile
dev_langs:
- C++
helpviewer_keywords:
- HTTP files
- HTTP requests, requesting and reading files
- CHttpFile class
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0077c04f53514901dccaa3d162cd132578270225
ms.lasthandoff: 02/24/2017

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
|[CHttpFile::CHttpFile](#chttpfile)|创建一个 `CHttpFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|将标头添加到发送到 HTTP 服务器的请求。|  
|[CHttpFile::EndRequest](#endrequest)|结束请求发送到 HTTP 服务器与[SendRequestEx](#sendrequestex)成员函数。|  
|[CHttpFile::GetFileURL](#getfileurl)|获取为指定的文件的 URL。|  
|[CHttpFile::GetObject](#getobject)|与 HTTP 服务器在请求中获取该谓词的目标对象。|  
|[CHttpFile::GetVerb](#getverb)|获取与 HTTP 服务器请求中使用的谓词。|  
|[CHttpFile::QueryInfo](#queryinfo)|从 HTTP 服务器返回的响应或请求标头。|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|检索与 HTTP 请求相关联的状态代码并将其放在提供`dwStatusCode`参数。|  
|[CHttpFile::SendRequest](#sendrequest)|将请求发送到 HTTP 服务器。|  
|[CHttpFile::SendRequestEx](#sendrequestex)|将请求发送到 HTTP 服务器使用[编写](../../mfc/reference/cinternetfile-class.md#write)或[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。|  
  
## <a name="remarks"></a>备注  
 如果 Internet 会话读取 HTTP 服务器中的数据，则必须创建的实例`CHttpFile`。  
  
 若要了解有关如何`CHttpFile`工作与其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="a-nameaddrequestheadersa--chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders  
 调用此成员函数添加一个或多个 HTTP 请求标头对 HTTP 请求处理。  
  
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
 指向包含标头或标头，以便将附加到请求的字符串的指针。 每个标头必须由 CR/LF 对结尾。  
  
 `dwFlags`  
 修改的新的标头的语义。 可以是以下各项之一：  
  
- `HTTP_ADDREQ_FLAG_COALESCE`将合并具有相同的名称，使用标记添加到后续的标头中找到的第一个标头的标头。 例如，"接受︰ 文本 / *"后跟"接受︰ 音频 /\*"形成单个标头将导致"接受︰ 文本 /\*、 音频 /\*"。 负责调用应用程序，确保对于收到的与合并或单独标头一起发送的请求数据的有凝聚力方案。  
  
- `HTTP_ADDREQ_FLAG_REPLACE`执行删除，并添加要替换当前标头。 标头名称将用于删除当前标头，并完整值将用于添加新的标头。 如果标头值为空并且找到该标头，将删除它。 如果不为空，则将替换标头值。  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW`如果不存在，只添加标头。 如果存在，则返回错误。  
  
- `HTTP_ADDREQ_FLAG_ADD`用于替换。 如果不存在，请添加标头。  
  
 `dwHeadersLen`  
 长度，以字符为单位的`pstrHeaders`。 如果这是-1l，则`pstrHeaders`被假定为零终止，并计算出的长度。  
  
 `str`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含请求标头或要添加的标头。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 `AddRequestHeaders`将附加的、 无格式标头追加到 HTTP 请求句柄。 它旨在供使用的复杂客户端需要对发送到 HTTP 服务器的精确请求细致的控制。  
  
> [!NOTE]
>  应用程序可以将多个标头中的传递`pstrHeaders`或`str`为`AddRequestHeaders`调用使用`HTTP_ADDREQ_FLAG_ADD`或`HTTP_ADDREQ_FLAG_ADD_IF_NEW`。 如果应用程序将尝试删除或替换标头使用**HTTP_ADDREQ_FLAG_REMOVE**或`HTTP_ADDREQ_FLAG_REPLACE`，只有一个页眉可以按提供`lpszHeaders`。  
  
##  <a name="a-namechttpfilea--chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile::CHttpFile  
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
 `hFile`  
 Internet 文件的句柄。  
  
 `hSession`  
 一个 Internet 会话句柄。  
  
 *pstrObject*  
 一个字符串，包含一个指向`CHttpFile`对象。  
  
 `pstrServer`  
 指向一个包含服务器的名称的字符串的指针。  
  
 `pstrVerb`  
 指向包含要发送请求时要使用的方法的字符串的指针。 Can be **POST**, **HEAD**, or `GET`.  
  
 dwContext  
 上下文标识符`CHttpFile`对象。 请参阅**备注**有关此参数的详细信息。  
  
 `pConnection`  
 一个指向[CHttpConnection](../../mfc/reference/chttpconnection-class.md)对象。  
  
### <a name="remarks"></a>备注  
 永远不会构造`CHttpFile`直接对象; 而是调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)相反。  
  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当您调用`CInternetSession::OpenURL`或`CHttpConnection`构造`CHttpFile`对象时，您可以重写默认设置，以便为您选择的值设置上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供对它标识的对象的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="a-nameendrequesta--chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile::EndRequest  
 调用此成员函数来结束发送到 HTTP 服务器所使用的请求[SendRequestEx](#sendrequestex)成员函数。  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 描述该操作的标志。 有关相应标志的列表，请参阅[HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpBuffIn`  
 指向已初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用来执行操作的输入的缓冲区。  
  
 `dwContext`  
 上下文标识符`CHttpFile`操作。 有关此参数的详细信息，请参阅备注。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查则引发该异常来确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当您调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)构造`CHttpFile`对象时，您可以重写默认设置，以便为您选择的值设置上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供对它标识的对象的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="a-namegetfileurla--chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile::GetFileURL  
 调用该成员函数以获取作为 URL 的 HTTP 文件的名称。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含引用与此文件关联的资源的 URL。  
  
### <a name="remarks"></a>备注  
 在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建的对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="a-namegetobjecta--chttpfilegetobject"></a><a name="getobject"></a>CHttpFile::GetObject  
 调用此成员函数以获取与此相关联的对象的名称`CHttpFile`。  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含的对象名称。  
  
### <a name="remarks"></a>备注  
 在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建的对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="a-namegetverba--chttpfilegetverb"></a><a name="getverb"></a>CHttpFile::GetVerb  
 调用此成员函数可获取与此相关的 HTTP 谓词 （或方法） `CHttpFile`。  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含 HTTP 谓词 （或方法） 的名称。  
  
### <a name="remarks"></a>备注  
 在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建的对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="a-namequeryinfoa--chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile::QueryInfo  
 调用该成员函数以返回响应或请求标头从 HTTP 请求。  
  
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
 对查询和指定的请求的信息类型的以下标志属性的组合︰  
  
- **HTTP_QUERY_CUSTOM**查找标头名称，并返回此值`lpvBuffer`输出。 **HTTP_QUERY_CUSTOM**如果未找到该标头，则引发断言。  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS**通常情况下，应用程序会查询响应标头，但应用程序还可以使用此标志的查询请求标头。  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME**这些标头，其值是一个日期/时间字符串，例如"上次修改时间，"为此标志返回的标头值与标准 Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)不需要应用程序分析的数据的结构。 如果您使用此标志，您可能想要使用`SYSTEMTIME`函数的重写。  
  
- **HTTP_QUERY_FLAG_NUMBER**此标志将数据作为 32 位数字返回其值是一个数字，例如状态代码，这些标头。  
  
 请参阅**备注**的可能值列表的部分。  
  
 `lpvBuffer`  
 指向接收信息的缓冲区的指针。  
  
 `lpdwBufferLength`  
 在进入时，这点到包含中的字符数或字节数据缓冲区的长度的值。 请参阅**备注**部分更多详细信息，有关此参数。  
  
 `lpdwIndex`  
 指向从零开始的标头索引的指针。 可以是**NULL**。 使用此标志枚举具有相同名称的多个标头。 在输入时，`lpdwIndex`指示要返回的指定标头的索引。 在输出时，`lpdwIndex`指示下一个标头的索引。 如果找不到下一个索引， **ERROR_HTTP_HEADER_NOT_FOUND**返回。  
  
 `str`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收返回的信息的对象。  
  
 `dwIndex`  
 一个索引值。 请参阅`lpdwIndex`。  
  
 *pSysTime*  
 一个指向 Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建的对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 您可以检索以下类型的数据从`QueryInfo`:  
  
-   字符串 （默认值）  
  
- `SYSTEMTIME`(有关"数据:""Expires:"等，标头)  
  
- `DWORD`(有关**STATUS_CODE**， **CONTENT_LENGTH**，等等。)  
  
 当字符串写入缓冲区，并且成员函数成功，`lpdwBufferLength`包含以字符为单位减 1 的终止的字符串的长度**NULL**字符。  
  
 可能的`dwInfoLevel`值包括︰  
  
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
  
##  <a name="a-namequeryinfostatuscodea--chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode  
 调用此成员函数以获取与 HTTP 请求相关联的状态代码并将其放在提供`dwStatusCode`参数。  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwStatusCode`  
 对一个状态代码的引用。 状态代码指示成功或失败的请求的事件。 请参阅**备注**为选定的状态代码说明。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 在成功调用后才使用此成员函数[SendRequest](#sendrequest)或在`CHttpFile`成功创建的对象[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 HTTP 状态代码分为组指示成功或失败的请求。 下表概述了状态代码组以及最常见的 HTTP 状态代码。  
  
|Group|含义|  
|-----------|-------------|  
|200-299|成功|  
|300-399|信息|  
|400-499|请求错误|  
|500-599|服务器错误|  
  
 常见的 HTTP 状态代码︰  
  
|状态代码|含义|  
|-----------------|-------------|  
|200|找到了 URL，接下来进行传输|  
|400|无法理解的请求|  
|404|找不到请求的 URL|  
|405|服务器不支持请求的方法|  
|500|未知的服务器错误|  
|503|已达到服务器容量|  
  
##  <a name="a-namesendrequesta--chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile::SendRequest  
 调用该成员函数以将请求发送到 HTTP 服务器。  
  
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
 要在请求标头后立即发送任何可选数据。 这通常适用于**POST**和**放**操作。 这可能是**NULL**如果没有要发送的可选数据。  
  
 *dwOptionalLen*  
 `lpOptional` 的长度。  
  
 `strHeaders`  
 包含正在发送的请求标头的名称的字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，则通过检查则引发该异常来确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
##  <a name="a-namesendrequestexa--chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::SendRequestEx  
 调用该成员函数以将请求发送到 HTTP 服务器。  
  
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
 描述该操作的标志。 有关相应标志的列表，请参阅[HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 `dwContext`  
 上下文标识符`CHttpFile`操作。 有关此参数的详细信息，请参阅备注。  
  
 `lpBuffIn`  
 指向已初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用来执行操作的输入的缓冲区。  
  
 *lpBuffOut*  
 指向已初始化**INTERNET_BUFFERS**描述用来执行操作的输出缓冲区。  
  
### <a name="return-value"></a>返回值  
 如果成功，非零值。 如果调用失败，则通过检查则引发该异常来确定失败的原因[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此函数允许应用程序通过发送数据[编写](../../mfc/reference/cinternetfile-class.md#write)和[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。 您必须知道要在调用此函数是重写之前发送的数据的长度。 可以使用第一个替代以指定想要将发送的数据的长度。 第二个重写接受指向**INTERNET_BUFFERS**结构，可用于描述缓冲区中大量的详细信息。  
  
 内容写入到文件后，调用[EndRequest](#endrequest)来取消操作。  
  
 默认值为`dwContext`发送到 mfc`CHttpFile`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CHttpFile`对象。 当您调用[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)构造`CHttpFile`对象时，您可以重写默认设置，以便为您选择的值设置上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供对它标识的对象的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
### <a name="example"></a>示例  
 此代码片段将一个字符串的内容发送到名为 MFCISAPI 的 DLL。在本地主机服务器上的 DLL。 虽然此示例中使用仅调用一个`WriteString`，是可接受的使用多个调用将数据发送在块中。  
  
 [!code-cpp[NVC_MFCWinInet #&9;](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)

