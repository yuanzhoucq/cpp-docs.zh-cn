---
title: 互联网 URL 解析全局和帮助器
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356609"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>互联网 URL 解析全局和帮助器

当某个客户端发送查询到 Internet 服务器时，您可以使用 URL 分析全局变量之一提取有关此客户端的信息。 帮助器功能提供其他互联网功能。

## <a name="internet-url-parsing-globals"></a>Internet URL 分析全局函数

|||
|-|-|
|[AfxParseURL](#afxparseurl)|分析 URL 字符串并返回服务类型及其组件。|
|[AfxParseURLEx](#afxparseurlex)|分析 URL 字符串并返回服务类型及其组件，这与提供用户名和密码一样。|

## <a name="other-internet-helpers"></a>其他互联网帮助

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|引发与互联网连接相关的异常。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|确定 Internet 句柄的类型。|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

此全局在[CInternetSession：：打开URL](../../mfc/reference/cinternetsession-class.md#openurl)中使用。

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
指向包含要解析的 URL 的字符串的指针。

*dwServiceType*<br/>
指示 Internet 服务的类型。 可能的值如下所示：

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

*斯特雷服务器*<br/>
服务类型之后 URL 的第一个段。

*strObject*<br/>
URL 引用的对象（可能为空）。

*n波特*<br/>
从 URL 的服务器或对象部分确定（如果存在）。

### <a name="return-value"></a>返回值

如果 URL 已成功解析，则非零;否则，如果为空或不包含已知的 Internet 服务类型，则为 0。

### <a name="remarks"></a>备注

它分析 URL 字符串并返回服务类型及其组件。

例如，`AfxParseURL`分析窗体*service://server/dir/dir/object.ext:port*的 URL 并返回存储的组件，如下所示：

*strServer* = "服务器"

*strObject* = "/dir/dir/dir/对象/对象.ext"

*n波特*= #port

*dwServiceType* = #service

> [!NOTE]
> 要调用此函数，您的项目必须包括 AFXINET。H。

### <a name="requirements"></a>要求

  **标题**afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

此全局函数是[AfxParseURL](#afxparseurl)的扩展版本，用于[CInternetSession：：openURL](../../mfc/reference/cinternetsession-class.md#openurl)。

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
指向包含要解析的 URL 的字符串的指针。

*dwServiceType*<br/>
指示 Internet 服务的类型。 可能的值如下所示：

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

*斯特雷服务器*<br/>
服务类型之后 URL 的第一个段。

*strObject*<br/>
URL 引用的对象（可能为空）。

*n波特*<br/>
从 URL 的服务器或对象部分确定（如果存在）。

*串用户名*<br/>
对包含用户名称`CString`的对象的引用。

*斯特密码*<br/>
对包含用户密码`CString`的对象的引用。

dwFlags**<br/>
控制如何分析 URL 的标志。 可以是以下值的组合：

|“值”|含义|
|-----------|-------------|
|ICU_DECODE|将 %XX 转义序列转换为字符。|
|ICU_NO_ENCODE|不要将不安全的字符转换为转义序列。|
|ICU_NO_META|不要删除元序列（如"*"。 和"*"。从 URL。|
|ICU_ENCODE_SPACES_ONLY|仅对空格进行编码。|
|ICU_BROWSER_MODE|不要在"+"或"""之后对字符进行编码或解码，也不要删除""之后的尾随空格。 如果未指定此值，则对整个 URL 进行编码并删除尾随空格。|

如果使用 MFC 默认值（没有标志），则函数将转换所有不安全的字符和元序列（如\\.、* . 和\\.）以转义序列。

### <a name="return-value"></a>返回值

如果 URL 已成功解析，则非零;否则，如果为空或不包含已知的 Internet 服务类型，则为 0。

### <a name="remarks"></a>备注

它解析 URL 字符串并返回服务类型及其组件，并提供用户的名称和密码。 这些标志指示如何处理不安全的字符。

> [!NOTE]
> 要调用此函数，您的项目必须包括 AFXINET。H。

### <a name="requirements"></a>要求

  **标题**afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGet互联网处理类型

使用此全局函数确定 Internet 句柄的类型。

### <a name="syntax"></a>语法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>参数

*hQuery*<br/>
Internet 查询的句柄。

### <a name="return-value"></a>返回值

WININET 定义的任何 Internet 服务类型。H。 有关这些互联网服务的列表，请参阅备注部分。 如果句柄为 NULL 或无法识别，则函数将返回AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>备注

以下列表包括 返回的可能`AfxGetInternetHandleType`Internet 类型。

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
> 为了调用此函数，您的项目必须包括 AFXINET。H。

### <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrow互联网例外

引发 Internet 异常。

### <a name="syntax"></a>语法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>参数

*dwContext*<br/>
导致错误的操作的上下文标识符。 *dwContext*的默认值最初在[CInternetSession 中](cinternetsession-class.md)指定，并传递给[CInternetConnection](cinternetconnection-class.md)- 和[CInternetFile](cinternetfile-class.md)派生类。 对于对连接或文件执行的特定操作，通常使用您自己的*dwContext*覆盖默认值。 然后，此值将返回到[CInternetSession：：onStatusBack](cinternetsession-class.md#onstatuscallback)以标识特定操作的状态。

*dwError*<br/>
导致异常的错误。

### <a name="remarks"></a>备注

您负责根据操作系统错误代码确定原因。

> [!NOTE]
> 要调用此函数，您的项目必须包括 AFXINET。H。

### <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[C 互联网例外类](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
