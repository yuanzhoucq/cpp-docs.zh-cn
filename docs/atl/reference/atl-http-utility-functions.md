---
title: ATL HTTP 实用工具函数
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: ca6dfdfb02f5ef629c6eb523744260f177a3309b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865015"
---
# <a name="atl-http-utility-functions"></a>ATL HTTP 实用工具函数

这些函数支持处理 Url。

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes URL，其中包括将不安全字符和空格转换为转义序列。|
|[AtlCombineUrl](#atlcombineurl)|将基 URL 和相对 URL 合并为单个规范 URL。|
|[AtlEscapeUrl](#atlescapeurl)|将所有不安全字符转换为转义序列。|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|获取与特定 Internet 协议或方案关联的默认端口号。|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|确定字符是否在 URL 中可安全使用。|
|[AtlUnescapeUrl](#atlunescapeurl)|将转义字符转换回其原始值。|
|[RGBToHtml](#rgbtohtml)|将[COLORREF](/windows/win32/gdi/colorref)值转换为与该颜色值相对应的 HTML 文本。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|调用此函数可将系统时间转换为采用适合在 HTTP 标头中使用的格式的字符串。|

## <a name="requirements"></a>要求

**标头：** atlutil

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl

调用此函数可对 URL 进行规范化，包括将不安全的字符和空格转换为转义序列。

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>parameters

*szUrl*<br/>
要规范化的 URL。

*szCanonicalized*<br/>
用于接收规范化 URL 的调用方分配的缓冲区。

*pdwMaxLength*<br/>
指向一个变量的指针，该变量包含*szCanonicalized*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数，包括终止 null 字符。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位），其中包括用于终止 null 字符的空间。

dwFlags<br/>
控制此函数行为的 ATL_URL 标志。

- ATL_URL_BROWSER_MODE 不会对 "#" 或 "？" 后面的字符进行编码或解码，也不会删除 "？" 后面的尾随空格。 如果未指定此值，则会对整个 URL 进行编码，并删除尾随空格。

- 在分析 URL 之前，ATL_URL_DECODE 将所有% XX 序列转换为字符，包括转义序列。

- ATL_URL_ENCODE_PERCENT 对遇到的任何百分号进行编码。 默认情况下，不对百分号进行编码。

- ATL_URL_ENCODE_SPACES_ONLY 仅对空格进行编码。

- ATL_URL_ESCAPE 将所有转义序列（% XX）转换为其对应的字符。

- ATL_URL_NO_ENCODE 不会将不安全字符转换为转义序列。

- ATL_URL_NO_META 不会从 URL 中删除元序列（如 "." 和 "..."）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

的行为类似于当前版本的[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) ，但不需要安装 WinInet 或 Internet Explorer。

## <a name="atlcombineurl"></a>AtlCombineUrl

调用此函数可将基 URL 和相对 URL 合并为单个规范 URL。

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>parameters

*szBaseUrl*<br/>
基本 URL。

*szRelativeUrl*<br/>
相对于基 URL 的 URL。

*szBuffer*<br/>
用于接收规范化 URL 的调用方分配的缓冲区。

*pdwMaxLength*<br/>
指向一个变量的指针，该变量包含*szBuffer*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数，包括终止 null 字符。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位），其中包括用于终止 null 字符的空间。

dwFlags<br/>
控制此函数的行为的标志。 请参阅[AtlCanonicalizeUrl](#atlcanonicalizeurl)。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

的行为类似于当前版本的[InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) ，但不需要安装 WinInet 或 Internet Explorer。

## <a name="atlescapeurl"></a>AtlEscapeUrl

调用此函数可将所有不安全字符转换为转义序列。

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>parameters

*lpszStringIn*<br/>
要转换的 URL。

*lpszStringOut*<br/>
调用方分配的缓冲区，转换后的 URL 将写入该缓冲区。

*pdwStrLen*<br/>
指向 DWORD 变量的指针。 如果函数成功， *pdwStrLen*将收到写入缓冲区的字符数，包括终止 null 字符。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位），其中包括用于终止 null 字符的空间。 使用此方法的宽字符版本时， *pdwStrLen*接收所需的字符数，而不是字节数。

*dwMaxLength*<br/>
缓冲区*lpszStringOut*的大小。

dwFlags<br/>
控制此函数行为的 ATL_URL 标志。 有关可能的值，请参阅[ATLCanonicalizeUrl](#atlcanonicalizeurl) 。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="atlgetdefaulturlport"></a>AtlGetDefaultUrlPort

调用此函数可获取与特定 Internet 协议或方案关联的默认端口号。

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>parameters

*m_nScheme*<br/>
标识要为其获取端口号的方案的[ATL_URL_SCHEME](atl-url-scheme-enum.md)值。

### <a name="return-value"></a>返回值

与指定方案或 ATL_URL_INVALID_PORT_NUMBER 关联的[ATL_URL_PORT](atl-typedefs.md#atl_url_port) （如果无法识别方案）。

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar

调用此函数可了解字符在 URL 中能否安全使用。

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>parameters

*下巴向上看*<br/>
要进行安全测试的字符。

### <a name="return-value"></a>返回值

如果输入字符不安全，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

可以使用此函数测试不应在 Url 中使用的字符，并使用[AtlCanonicalizeUrl](#atlcanonicalizeurl)进行转换。

## <a name="atlunescapeurl"></a>AtlUnescapeUrl

调用此函数可将转义字符转换为其原始值。

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>parameters

*lpszStringIn*<br/>
要转换的 URL。

*lpszStringOut*<br/>
调用方分配的缓冲区，转换后的 URL 将写入该缓冲区。

*pdwStrLen*<br/>
指向 DWORD 变量的指针。 如果该函数成功，则该变量将接收写入缓冲区的字符数，包括终止 null 字符。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位），其中包括用于终止 null 字符的空间。

*dwMaxLength*<br/>
缓冲区*lpszStringOut*的大小。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

反转[AtlEscapeUrl](#atlescapeurl)应用的转换过程。

## <a name="rgbtohtml"></a>RGBToHtml

将[COLORREF](/windows/win32/gdi/colorref)值转换为与该颜色值相对应的 HTML 文本。

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>parameters

*颜色*<br/>
RGB 颜色值。

*pbOut*<br/>
调用方分配的缓冲区，用于接收 HTML 颜色值的文本。 缓冲区的空间必须至少包含8个字符，包括空终止符的空格）。

*nBuffer*<br/>
缓冲区的大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

HTML 颜色值是一个井号，后跟一个6位数的十六进制值，它对颜色的每个红色、绿色和蓝色分量使用2个数字（例如，#FFFFFF 为白色）。

## <a name="systemtimetohttpdate"></a>SystemTimeToHttpDate

调用此函数可将系统时间转换为采用适合在 HTTP 标头中使用的格式的字符串。

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>parameters

*停止*<br/>
要作为 HTTP 格式字符串获取的系统时间。

*strTime*<br/>
对字符串变量的引用，该变量用于接收 RFC 2616 （[https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)）和 rfc 1123 （[https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)）中定义的 HTTP 日期时间。

## <a name="see-also"></a>另请参阅

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
