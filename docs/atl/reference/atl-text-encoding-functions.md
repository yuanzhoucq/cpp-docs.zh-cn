---
title: ATL 文本编码函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b77c814b3ce2f372ae34e3c0293951ec23cdf6a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090745"
---
# <a name="atl-text-encoding-functions"></a>ATL 文本编码函数

这些函数支持文本编码和解码。

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|调用此函数可获取十六进制数字的数值。|
|[AtlGetVersion](#atlgetversion)|调用此函数可获取使用 ATL 库的版本。  |
|[AtlHexDecode](#atlhexdecode)|对通过以前调用编码为十六进制文本的数据的字符串解码[AtlHexEncode](#atlhexencode)。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。|
|[AtlHexEncode](#atlhexencode)|调用此函数可将某些数据编码为十六进制文本的字符串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[AtlHexValue](#atlhexvalue)|调用此函数可获取十六进制数字的数值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|调用此函数可将 Unicode 字符串转换为 UTF-8。 |
|[BEncode](#bencode)|调用此函数可转换使用“B”编码的某些数据。|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[EscapeXML](#escapexml)|调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。|
|[GetExtendedChars](#getextendedchars)|调用此函数可获取字符串中的扩展字符的数目。|
|[IsExtendedChar](#isextendedchar)|调用此函数可了解给定字符是否为扩展字符（小于 32、大于 126，并且不是制表符、换行符或回车符）|
|[QEncode](#qencode)|调用此函数可转换使用“Q”编码的某些数据。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[QPDecode](#qpdecode)|对通过以前调用编码 quoted printable 格式的数据的字符串解码[QPEncode](#qpencode)。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。|
|[QPEncode](#qpencode)|调用此函数可对某些 Quoted Printable 格式的数据进行编码。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[取消解码](#uudecode)|对已进行 uuencode 如通过以前调用的数据的字符串解码[UUEncode](#uuencode)。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。|
|[UUEncode](#uuencode)|调用此函数可对某些数据进行 uuencode。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|

## <a name="requirements"></a>要求

**标头：** atlenc.h

## <a name="atlgethexvalue"></a> AtlGetHexValue

调用此函数可获取十六进制数字的数值。

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>参数

*下巴*<br/>
十六进制字符"0"-"9"、 A-F 或 a-f。

### <a name="return-value"></a>返回值

输入字符解释为十六进制数字的数值。 例如，"0"的输入返回值为 0 和 A 的输入返回值为 10。 如果输入的字符不是十六进制数字，则此函数将返回-1。

## <a name="atlgetversion"></a> AtlGetVersion

调用此函数可获取使用 ATL 库的版本。

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>参数

*保留*<br/>
保留的指针。

### <a name="return-value"></a>返回值

返回正在编译或运行 ATL 库的版本的 DWORD 的整数值。

## <a name="example"></a>示例

应按如下所示调用的函数。

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="atlhexdecode"></a> AtlHexDecode

对通过以前调用编码为十六进制文本的数据的字符串解码[AtlHexEncode](#atlhexencode)。

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>参数

*pSrcData*<br/>
包含要解码的数据的字符串。

*nSrcLen*<br/>
以字符为单位的长度*pSrcData*。

*pbDest*<br/>
用于接收已解码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含以字节为单位的长度的变量*pbDest*。 如果函数成功，则该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所需的长度以字节为单位的缓冲区。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

## <a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
已编码的字符串中的字符数。

### <a name="return-value"></a>返回值

可以保存的已解码的字符串的缓冲区所需的字节数*nSrcLen*字符。

## <a name="atlhexencode"></a> AtlHexEncode

调用此函数可将某些数据编码为十六进制文本的字符串。

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要编码的数据的缓冲区。

*nSrcLen*<br/>
要进行编码的数据长度以字节为单位。

*szDest*<br/>
用于接收编码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含的字符长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收所需的长度以字符为单位的缓冲区。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

源数据的每个字节编码为 2 个十六进制字符。

## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
数据进行编码的字节数。

### <a name="return-value"></a>返回值

无法保存的已编码的数据的缓冲区所需的字符数*nSrcLen*字节。

## <a name="atlhexvalue"></a> AtlHexValue

调用此函数可获取十六进制数字的数值。

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>参数

*下巴*<br/>
十六进制字符"0"-"9"、 A-F 或 a-f。

### <a name="return-value"></a>返回值

输入字符解释为十六进制数字的数值。 例如，"0"的输入返回值为 0 和 A 的输入返回值为 10。 如果输入的字符不是十六进制数字，则此函数将返回-1。

## <a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8

调用此函数可将 Unicode 字符串转换为 UTF-8。

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>参数

*wszSrc*<br/>
要转换的 Unicode 字符串

*nSrc*<br/>
中的 Unicode 字符串的字符长度。

*szDest*<br/>
若要接收转换后的字符串的调用方分配的缓冲区。

*nDest*<br/>
缓冲区的长度以字节为单位。

### <a name="return-value"></a>返回值

返回转换后的字符串的字符数。

### <a name="remarks"></a>备注

若要确定所需的转换后的字符串缓冲区的大小，请调用此函数传递 0 *szDest*并*nDest*。

## <a name="bencode"></a> BEncode

调用此函数可转换使用“B”编码的某些数据。

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要编码的数据的缓冲区。

*nSrcLen*<br/>
要进行编码的数据长度以字节为单位。

*szDest*<br/>
用于接收编码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含的字符长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收所需的长度以字符为单位的缓冲区。

*pszCharSet*<br/>
要使用用于转换的字符集。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

"B"编码方案在 RFC 最多允许 2047年中所述 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。

## <a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
数据进行编码的字节数。

*nCharsetLen*<br/>
以字符为单位设置为使用用于转换的字符的长度。

### <a name="return-value"></a>返回值

无法保存的已编码的数据的缓冲区所需的字符数*nSrcLen*字节。

### <a name="remarks"></a>备注

"B"编码方案在 RFC 最多允许 2047年中所述 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。

## <a name="escapexml"></a> EscapeXML

调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>参数

*szIn*<br/>
要转换的字符串。

*nSrclen*<br/>
中要转换的字符串的字符长度。

*szEsc*<br/>
若要接收转换后的字符串的调用方分配的缓冲区。

*nDestLen*<br/>
以字符为单位的调用方分配的缓冲区长度。

*dwFlags*<br/>
描述如何执行转换的 ATL_ESC 标志。

- ATL_ESC_FLAG_NONE 默认行为。 引号标记和撇号不会转换。
- ATL_ESC_FLAG_ATTR 用引号括起来的标记和撇号转换为`&quot;`和`&apos;`分别。

### <a name="return-value"></a>返回值

在转换后的字符串的字符长度。

### <a name="remarks"></a>备注

可能的转换执行此函数的表所示：

|源|目标|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a> GetExtendedChars

调用此函数可获取字符串中的扩展字符的数目。

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>参数

*szSrc*<br/>
要对其进行分析的字符串。

*nSrcLen*<br/>
以字符为单位的字符串的长度。

### <a name="return-value"></a>返回值

返回由字符串中找到的扩展字符数目[IsExtendedChar](#isextendedchar)。

## <a name="isextendedchar"></a> IsExtendedChar

调用此函数可了解给定字符是否为扩展字符（小于 32、大于 126，并且不是制表符、换行符或回车符）

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>参数

*ch*<br/>
要进行测试的字符

### <a name="return-value"></a>返回值

如果字符已扩展，则返回 FALSE 否则，则为 TRUE。

## <a name="qencode"></a> QEncode

调用此函数可转换使用“Q”编码的某些数据。

```
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要编码的数据的缓冲区。

*nSrcLen*<br/>
要进行编码的数据长度以字节为单位。

*szDest*<br/>
用于接收编码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含的字符长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收所需的长度以字符为单位的缓冲区。

*pszCharSet*<br/>
要使用用于转换的字符集。

*pnNumEncoded*<br/>
指向包含的变量在返回的不安全必须要转换的字符数的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

"Q"编码方案在 RFC 最多允许 2047年中所述 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。

## <a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
数据进行编码的字节数。

*nCharsetLen*<br/>
以字符为单位设置为使用用于转换的字符的长度。

### <a name="return-value"></a>返回值

无法保存的已编码的数据的缓冲区所需的字符数*nSrcLen*字节。

### <a name="remarks"></a>备注

"Q"编码方案在 RFC 最多允许 2047年中所述 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。

## <a name="qpdecode"></a> QPDecode

对通过以前调用编码 quoted printable 格式的数据的字符串解码[QPEncode](#qpencode)。

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
[in]包含要解码的数据的缓冲区。

*nSrcLen*<br/>
[in]以字节为单位的长度*pbSrcData*。

*szDest*<br/>
[out]用于接收已解码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
[out]指向包含以字节为单位的长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所需的长度以字节为单位的缓冲区。

*dwFlags*<br/>
[in]描述如何执行转换的 ATLSMTP_QPENCODE 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。

## <a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
已编码的字符串中的字符数。

### <a name="return-value"></a>返回值

可以保存的已解码的字符串的缓冲区所需的字节数*nSrcLen*字符。

### <a name="remarks"></a>备注

RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。

## <a name="qpencode"></a> QPEncode

调用此函数可对某些 Quoted Printable 格式的数据进行编码。

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要编码的数据的缓冲区。

*nSrcLen*<br/>
要进行编码的数据长度以字节为单位。

*szDest*<br/>
用于接收编码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含的字符长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收所需的长度以字符为单位的缓冲区。

*dwFlags*<br/>
描述如何执行转换的 ATLSMTP_QPENCODE 标志。

- 一段 ATLSMTP_QPENCODE_DOT 如果出现在行的开头，它是添加到输出，以及编码。

- ATLSMTP_QPENCODE_TRAILING_SOFT 追加`=\r\n`到编码的字符串。

Quoted printable 编码方案中所述[RFC 2045](http://www.ietf.org/rfc/rfc2045.txt)。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。

## <a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
数据进行编码的字节数。

### <a name="return-value"></a>返回值

无法保存的已编码的数据的缓冲区所需的字符数*nSrcLen*字节。

### <a name="remarks"></a>备注

RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。

## <a name="uudecode"></a> 取消解码

对已进行 uuencode 如通过以前调用的数据的字符串解码[UUEncode](#uuencode)。

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要解码的数据的字符串。

*nSrcLen*<br/>
以字节为单位的长度*pbSrcData*。

*pbDest*<br/>
用于接收已解码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含以字节为单位的长度的变量*pbDest*。 如果函数成功，则该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所需的长度以字节为单位的缓冲区。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。

## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
已编码的字符串中的字符数。

### <a name="return-value"></a>返回值

可以保存的已解码的字符串的缓冲区所需的字节数*nSrcLen*字符。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。

## <a name="uuencode"></a> UUEncode

调用此函数可对某些数据进行 uuencode。

```
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>参数

*pbSrcData*<br/>
包含要编码的数据的缓冲区。

*nSrcLen*<br/>
要进行编码的数据长度以字节为单位。

*szDest*<br/>
用于接收编码的数据的调用方分配的缓冲区。

*pnDestLen*<br/>
指向包含的字符长度的变量*szDest*。 如果函数成功，则该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收所需的长度以字符为单位的缓冲区。

*lpszFile*<br/>
文件中指定 ATLSMTP_UUENCODE_HEADER 时要添加到标头*dwFlags*。

*dwFlags*<br/>
控制此函数的行为的标志。

- 将编码 ATLSMTP_UUENCODE_HEADE 标头。

- 将编码 ATLSMTP_UUENCODE_END 结束。

- 将执行 ATLSMTP_UUENCODE_DOT 数据部分有关封装。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。

## <a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>参数

*nSrcLen*<br/>
数据进行编码的字节数。

### <a name="return-value"></a>返回值

无法保存的已编码的数据的缓冲区所需的字符数*nSrcLen*字节。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。

### <a name="see-also"></a>请参阅

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
