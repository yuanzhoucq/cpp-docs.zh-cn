---
title: Internet URL 分析全局和帮助程序
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865803"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet URL 分析全局和帮助程序

当某个客户端发送查询到 Internet 服务器时，您可以使用 URL 分析全局变量之一提取有关此客户端的信息。 Helper 函数提供其他 internet 功能。

## <a name="internet-url-parsing-globals"></a>Internet URL 分析全局函数

|||
|-|-|
|[AfxParseURL](#afxparseurl)|分析 URL 字符串并返回服务类型及其组件。|
|[AfxParseURLEx](#afxparseurlex)|分析 URL 字符串并返回服务类型及其组件，这与提供用户名和密码一样。|

## <a name="other-internet-helpers"></a>其他 Internet 帮助器

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|引发与 internet 连接相关的异常。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|确定 Internet 句柄的类型。|

##  <a name="afxparseurl"></a>AfxParseURL

此全局在[CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)中使用。

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>参数

*pstrURL*<br/>
一个指针，指向包含要分析的 URL 的字符串。

*dwServiceType*<br/>
指示 Internet 服务的类型。 可能的值如下：

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
服务类型后面的 URL 的第一段。

*strObject*<br/>
URL 引用的对象（可能为空）。

*nPort*<br/>
如果存在，则从 URL 的服务器或对象部分确定。

### <a name="return-value"></a>返回值

如果已成功分析 URL，则为非零值;否则，为0（如果它为空或不包含已知的 Internet 服务类型）。

### <a name="remarks"></a>备注

它分析 URL 字符串并返回服务类型及其组件。

例如，`AfxParseURL` 分析窗体*service://server/dir/dir/object.ext:port*的 url，并按如下所示返回存储的组件：

*strServer* = = "server"

*strObject* = = "/dir/dir/object/object.ext"

*nPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
>  若要调用此函数，你的项目必须包含 AFXINET.H。高.

### <a name="requirements"></a>要求

  **标头**afxinet。h

##  <a name="afxparseurlex"></a>AfxParseURLEx

此全局函数是[AfxParseURL](#afxparseurl)的扩展版本，在[CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)中使用。

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>参数

*pstrURL*<br/>
一个指针，指向包含要分析的 URL 的字符串。

*dwServiceType*<br/>
指示 Internet 服务的类型。 可能的值如下：

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
服务类型后面的 URL 的第一段。

*strObject*<br/>
URL 引用的对象（可能为空）。

*nPort*<br/>
如果存在，则从 URL 的服务器或对象部分确定。

*strUsername*<br/>
对包含用户名称的 `CString` 对象的引用。

*strPassword*<br/>
对包含用户密码的 `CString` 对象的引用。

dwFlags<br/>
控制如何分析 URL 的标志。 可以是以下值的组合：

|值|含义|
|-----------|-------------|
|ICU_DECODE|将% XX 转义序列转换为个字符。|
|ICU_NO_ENCODE|不要将不安全字符转换为转义序列。|
|ICU_NO_META|不要删除元序列（如 "\." 和 "\."）从 URL。|
|ICU_ENCODE_SPACES_ONLY|仅对空格编码。|
|ICU_BROWSER_MODE|不要对 "#" 或 "" 后的字符进行编码或解码，也不要删除 "" 后的尾随空格。 如果未指定此值，则会对整个 URL 进行编码，并删除尾随空格。|

如果使用 MFC 默认值（即无标志），则函数会将所有不安全字符和元序列（如 \\.、\. 和 \\...）转换为转义序列。

### <a name="return-value"></a>返回值

如果已成功分析 URL，则为非零值;否则，为0（如果它为空或不包含已知的 Internet 服务类型）。

### <a name="remarks"></a>备注

它分析 URL 字符串并返回服务类型及其组件，并提供用户的名称和密码。 标志指示如何处理不安全字符。

> [!NOTE]
>  若要调用此函数，你的项目必须包含 AFXINET.H。高.

### <a name="requirements"></a>要求

  **标头**afxinet。h

## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

使用此全局函数确定 Internet 句柄的类型。

### <a name="syntax"></a>语法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>参数

*hQuery*<br/>
Internet 查询的句柄。

### <a name="return-value"></a>返回值

WININET 定义的任何 Internet 服务类型。高. 有关这些 Internet 服务的列表，请参阅 "备注" 部分。 如果句柄为空或无法识别，则函数返回 AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>备注

以下列表包括 `AfxGetInternetHandleType`返回的可能的 Internet 类型。

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  为了调用此函数，你的项目必须包含 AFXINET.H。高.

### <a name="requirements"></a>要求

**标头：** afxinet。h

## <a name="afxthrowinternetexception"></a>AfxThrowInternetException

引发 Internet 异常。

### <a name="syntax"></a>语法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>参数

*dwContext*<br/>
导致错误的操作的上下文标识符。 *DwContext*的默认值最初指定在[CInternetSession](cinternetsession-class.md)中，并传递给[CInternetConnection](cinternetconnection-class.md)和[CInternetFile](cinternetfile-class.md)派生的类。 对于在连接或文件上执行的特定操作，通常使用自己的*dwContext*替代默认值。 此值随后返回到[CInternetSession：： OnStatusCallback](cinternetsession-class.md#onstatuscallback)以标识特定操作的状态。

*dwError*<br/>
导致异常的错误。

### <a name="remarks"></a>备注

你负责根据操作系统错误代码确定原因。

> [!NOTE]
>  若要调用此函数，你的项目必须包含 AFXINET.H。高.

### <a name="requirements"></a>要求

**标头：** afxinet。h

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[CInternetException 类](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
