---
title: Internet URL 分析全局函数和帮助程序
ms.date: 04/03/2017
f1_keywords:
- vc.mfc.macros.isapi
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 0831d94f1a6f0293d3605a5e2e9ebde0564baf24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321996"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet URL 分析全局函数和帮助程序

当某个客户端发送查询到 Internet 服务器时，您可以使用 URL 分析全局变量之一提取有关此客户端的信息。 帮助器函数提供其他 internet 功能。

## <a name="internet-url-parsing-globals"></a>Internet URL 分析全局函数

|||
|-|-|
|[AfxParseURL](#afxparseurl)|分析 URL 字符串并返回服务类型及其组件。|
|[AfxParseURLEx](#afxparseurlex)|分析 URL 字符串并返回服务类型及其组件，这与提供用户名和密码一样。|

## <a name="other-internet-helpers"></a>其他 Internet 帮助程序

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|引发与 internet 连接有关的异常。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|确定 Internet 句柄的类型。|

##  <a name="afxparseurl"></a>  AfxParseURL

在中使用此全局[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。

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
指向包含要分析的 URL 的字符串的指针。

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
以下服务类型的 URL 的第一个段。

*strObject*<br/>
URL 引用的对象 （可能为空）。

*nPort*<br/>
从服务器或对象部分 URL，确定是否存在。

### <a name="return-value"></a>返回值

已成功分析该 URL; 如果非零值否则为 0，如果它为空或不包含已知的 Internet 服务类型。

### <a name="remarks"></a>备注

它将分析 URL 字符串并返回服务及其组件的类型。

例如，`AfxParseURL`分析的窗体的 Url *service://server/dir/dir/object.ext:port*并返回其存储，如下所示：

*strServer* == "server"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
>  若要调用此函数，你的项目必须包括 AFXINET。H.

### <a name="requirements"></a>要求

  **标头**afxinet.h

##  <a name="afxparseurlex"></a>  AfxParseURLEx

此全局函数是扩展的版本[AfxParseURL](#afxparseurl) ，并在[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。

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
指向包含要分析的 URL 的字符串的指针。

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
以下服务类型的 URL 的第一个段。

*strObject*<br/>
URL 引用的对象 （可能为空）。

*nPort*<br/>
从服务器或对象部分 URL，确定是否存在。

*strUsername*<br/>
对引用`CString`对象，其中包含的用户的名称。

*strPassword*<br/>
对引用`CString`对象，其中包含的用户的密码。

*dwFlags*<br/>
控制如何分析的 URL 的标志。 可以是以下值的组合：

|“值”|含义|
|-----------|-------------|
|ICU_DECODE|将 %xx 转义序列转换为字符。|
|ICU_NO_ENCODE|不会转换不安全字符进行转义序列。|
|ICU_NO_META|不删除元序列 （例如"\"。 和"\..."）从 URL。|
|ICU_ENCODE_SPACES_ONLY|对仅空格进行编码。|
|ICU_BROWSER_MODE|不进行编码或解码字符后 '#' 或 '，但不删除尾随空格后 '。 如果未指定此值，编码整个 URL，并删除尾随空格。|

如果您使用 MFC 默认情况下，这不是任何标志，该函数将转换所有不安全字符和 meta 序列 (如\\。，\...，和\\...) 进行转义序列。

### <a name="return-value"></a>返回值

已成功分析该 URL; 如果非零值否则为 0，如果它为空或不包含已知的 Internet 服务类型。

### <a name="remarks"></a>备注

它将分析 URL 字符串并返回类型的服务和及其组件，以及提供用户的名称和密码。 这些标志指示如何不安全字符处理。

> [!NOTE]
>  若要调用此函数，你的项目必须包括 AFXINET。H.

### <a name="requirements"></a>要求

  **标头**afxinet.h

## <a name="afxgetinternethandletype"></a>  AfxGetInternetHandleType

使用此全局函数来确定 Internet 句柄的类型。

### <a name="syntax"></a>语法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>参数

*hQuery*<br/>
句柄 Internet 查询。

### <a name="return-value"></a>返回值

任何定义的 WININET Internet 服务类型。H. 请参阅这些 Internet 服务的列表的备注部分。 如果句柄为 NULL 或无法识别，该函数将返回 AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>备注

下面列出了可能的 Internet 类型返回的`AfxGetInternetHandleType`。

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
>  若要调用此函数，你的项目必须包括 AFXINET。H.

### <a name="requirements"></a>要求

**标头：** afxinet.h

## <a name="afxthrowinternetexception"></a>  AfxThrowInternetException

引发 Internet 异常。

### <a name="syntax"></a>语法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>参数

*dwContext*<br/>
导致错误的操作上下文标识符。 默认值*dwContext*中最初指定[CInternetSession](cinternetsession-class.md) ，并传递给[CInternetConnection](cinternetconnection-class.md)-和[CInternetFile](cinternetfile-class.md)的派生类。 对于连接或文件上执行特定操作，您通常覆盖与默认*dwContext*你自己。 然后此值将返回到[CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback)来标识特定操作的状态。

*dwError*<br/>
导致异常的错误。

### <a name="remarks"></a>备注

您负责确定基于操作系统错误代码的原因。

> [!NOTE]
>  若要调用此函数，你的项目必须包括 AFXINET。H.

### <a name="requirements"></a>要求

**标头：** afxinet.h

## <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)<br/>
[CInternetException 类](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
