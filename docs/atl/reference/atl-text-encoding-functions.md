---
title: ATL 文本编码函数
ms.date: 11/04/2016
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
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423524"
---
# <a name="atl-text-encoding-functions"></a>ATL 文本编码函数

这些函数支持文本编码和解码。

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|调用此函数可获取十六进制数字的数值。|
|[AtlGetVersion](#atlgetversion)|调用此函数可获取正在使用的 ATL 库的版本。  |
|[AtlHexDecode](#atlhexdecode)|对已编码为十六进制文本的数据字符串进行解码，如上一次对[AtlHexEncode](#atlhexencode)的调用。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。|
|[AtlHexEncode](#atlhexencode)|调用此函数可将某些数据编码为十六进制文本的字符串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[AtlHexValue](#atlhexvalue)|调用此函数可获取十六进制数字的数值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|调用此函数可将 Unicode 字符串转换为 UTF-8。 |
|[BEncode](#bencode)|调用此函数可转换使用“B”编码的某些数据。|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[EscapeXML](#escapexml)|调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。|
|[GetExtendedChars](#getextendedchars)|调用此函数可获取字符串中的扩展字符的数目。|
|[IsExtendedChar](#isextendedchar)|调用此函数可查明给定字符是否是扩展字符（小于32，大于126，而不是制表符、换行符或回车符）|
|[QEncode](#qencode)|调用此函数可转换使用“Q”编码的某些数据。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[QPDecode](#qpdecode)|对已使用带引号的可打印格式进行编码的数据字符串进行解码，如以前对[QPEncode](#qpencode)的调用。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。|
|[QPEncode](#qpencode)|调用此函数可对某些 Quoted Printable 格式的数据进行编码。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[UUDecode](#uudecode)|对已 uuencode 的数据字符串进行解码，如上一次调用[UUEncode](#uuencode)。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。|
|[UUEncode](#uuencode)|调用此函数可对某些数据进行 uuencode。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|

## <a name="requirements"></a>要求

**标头：** atlenc

## <a name="atlgethexvalue"></a>AtlGetHexValue

调用此函数可获取十六进制数字的数值。

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>parameters

*下巴向上看*<br/>
十六进制字符 "0"-"9"、"a-'F" 或 "a-'F"。

### <a name="return-value"></a>返回值

解释为十六进制数字的输入字符的数值。 例如，"0" 的输入返回值0，输入 "A" 返回值10。 如果输入字符不是十六进制数字，则此函数将返回-1。

## <a name="atlgetversion"></a>AtlGetVersion

调用此函数可获取正在使用的 ATL 库的版本。

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>parameters

*丢失*<br/>
保留指针。

### <a name="return-value"></a>返回值

返回正在编译或运行的 ATL 库版本的 DWORD 整数值。

## <a name="example"></a>示例

应按如下所示调用函数。

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="atlhexdecode"></a>AtlHexDecode

对已编码为十六进制文本的数据字符串进行解码，如上一次对[AtlHexEncode](#atlhexencode)的调用。

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>parameters

*pSrcData*<br/>
包含要解码的数据的字符串。

*nSrcLen*<br/>
*PSrcData*中的字符的长度。

*pbDest*<br/>
调用方分配的缓冲区，用于接收已解码的数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*pbDest*的长度（以字节为单位）。 如果该函数成功，则该变量将接收写入缓冲区的字节数。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
编码字符串中的字符数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字符的已解码字符串的缓冲区所需的字节数。

## <a name="atlhexencode"></a>AtlHexEncode

调用此函数可将某些数据编码为十六进制文本的字符串。

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要进行编码的数据的缓冲区。

*nSrcLen*<br/>
要编码的数据的长度（以字节为单位）。

*szDest*<br/>
调用方分配的缓冲区，用于接收编码数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*szDest*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数。 如果函数失败，则变量接收缓冲区的所需长度（以字符为限）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

源数据的每个字节都编码为两个十六进制字符。

## <a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
要编码的数据的字节数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字节编码数据的缓冲区所需的字符数。

## <a name="atlhexvalue"></a>AtlHexValue

调用此函数可获取十六进制数字的数值。

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>parameters

*下巴向上看*<br/>
十六进制字符 "0"-"9"、"a-'F" 或 "a-'F"。

### <a name="return-value"></a>返回值

解释为十六进制数字的输入字符的数值。 例如，"0" 的输入返回值0，输入 "A" 返回值10。 如果输入字符不是十六进制数字，则此函数将返回-1。

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

调用此函数可将 Unicode 字符串转换为 UTF-8。

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>parameters

*wszSrc*<br/>
要转换的 Unicode 字符串

*nSrc*<br/>
Unicode 字符串的长度（以字符为字符）。

*szDest*<br/>
调用方分配的缓冲区，用于接收转换后的字符串。

*nDest*<br/>
缓冲区的长度（以字节为单位）。

### <a name="return-value"></a>返回值

返回转换后的字符串的字符数。

### <a name="remarks"></a>备注

若要确定转换后的字符串所需的缓冲区大小，请调用此函数，将*szDest*和*nDest*传递给0。

## <a name="bencode"></a>BEncode

调用此函数可转换使用“B”编码的某些数据。

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要进行编码的数据的缓冲区。

*nSrcLen*<br/>
要编码的数据的长度（以字节为单位）。

*szDest*<br/>
调用方分配的缓冲区，用于接收编码数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*szDest*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数。 如果函数失败，则变量接收缓冲区的所需长度（以字符为限）。

*pszCharSet*<br/>
要用于转换的字符集。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

RFC 2047 中描述了 "B" 编码方案（[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）。

## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
要编码的数据的字节数。

*nCharsetLen*<br/>
要用于转换的字符集的长度（字符）。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字节编码数据的缓冲区所需的字符数。

### <a name="remarks"></a>备注

RFC 2047 中描述了 "B" 编码方案（[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）。

## <a name="escapexml"></a>EscapeXML

调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>parameters

*szIn*<br/>
要转换的字符串。

*nSrclen*<br/>
要转换的字符串的长度（以字符为字符）。

*szEsc*<br/>
调用方分配的缓冲区，用于接收转换后的字符串。

*nDestLen*<br/>
调用方分配的缓冲区的长度（以字符为字符）。

dwFlags<br/>
描述如何执行转换的 ATL_ESC 标志。

- ATL_ESC_FLAG_NONE 的默认行为。 引号和撇号不会转换。
- ATL_ESC_FLAG_ATTR 引号和撇号分别转换为 `&quot;` 和 `&apos;`。

### <a name="return-value"></a>返回值

转换后的字符串的长度（以字符为字符）。

### <a name="remarks"></a>备注

此函数所执行的转换可能在表中显示：

|源|目标|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>GetExtendedChars

调用此函数可获取字符串中的扩展字符的数目。

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>parameters

*szSrc*<br/>
要分析的字符串。

*nSrcLen*<br/>
字符串的长度（以字符为限）。

### <a name="return-value"></a>返回值

返回[IsExtendedChar](#isextendedchar)确定的字符串中找到的扩展字符数。

## <a name="isextendedchar"></a>IsExtendedChar

调用此函数可查明给定字符是否是扩展字符（小于32，大于126，而不是制表符、换行符或回车符）

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>parameters

*48*<br/>
要测试的字符

### <a name="return-value"></a>返回值

如果字符是扩展的，则为 TRUE; 否则为 FALSE。

## <a name="qencode"></a>QEncode

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

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要进行编码的数据的缓冲区。

*nSrcLen*<br/>
要编码的数据的长度（以字节为单位）。

*szDest*<br/>
调用方分配的缓冲区，用于接收编码数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*szDest*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数。 如果函数失败，则变量接收缓冲区的所需长度（以字符为限）。

*pszCharSet*<br/>
要用于转换的字符集。

*pnNumEncoded*<br/>
指向返回的变量的指针包含必须转换的不安全字符的数目。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

RFC 2047 中描述了 "Q" 编码方案（[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）。

## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
要编码的数据的字节数。

*nCharsetLen*<br/>
要用于转换的字符集的长度（字符）。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字节编码数据的缓冲区所需的字符数。

### <a name="remarks"></a>备注

RFC 2047 中描述了 "Q" 编码方案（[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）。

## <a name="qpdecode"></a>QPDecode

对已使用带引号的可打印格式进行编码的数据字符串进行解码，如以前对[QPEncode](#qpencode)的调用。

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
中包含要解码的数据的缓冲区。

*nSrcLen*<br/>
中*PbSrcData*的长度（以字节为单位）。

*szDest*<br/>
弄调用方分配的缓冲区，用于接收已解码的数据。

*pnDestLen*<br/>
弄指向一个变量的指针，该变量包含*szDest*的长度（以字节为单位）。 如果该函数成功，则该变量将接收写入缓冲区的字节数。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位）。

dwFlags<br/>
中描述如何执行转换的 ATLSMTP_QPENCODE 标志。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

RFC 2045 中描述了带引号的可打印编码方案（[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）。

## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
编码字符串中的字符数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字符的已解码字符串的缓冲区所需的字节数。

### <a name="remarks"></a>备注

RFC 2045 中描述了带引号的可打印编码方案（[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）。

## <a name="qpencode"></a>QPEncode

调用此函数可对某些 Quoted Printable 格式的数据进行编码。

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要进行编码的数据的缓冲区。

*nSrcLen*<br/>
要编码的数据的长度（以字节为单位）。

*szDest*<br/>
调用方分配的缓冲区，用于接收编码数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*szDest*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数。 如果函数失败，则变量接收缓冲区的所需长度（以字符为限）。

dwFlags<br/>
描述如何执行转换的 ATLSMTP_QPENCODE 标志。

- ATLSMTP_QPENCODE_DOT 如果句点出现在行的开头，则会将其添加到输出中并进行编码。

- ATLSMTP_QPENCODE_TRAILING_SOFT 追加 `=\r\n` 编码的字符串。

[RFC 2045](https://www.ietf.org/rfc/rfc2045.txt)中描述了带引号的可打印编码方案。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

RFC 2045 中描述了带引号的可打印编码方案（[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）。

## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
要编码的数据的字节数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字节编码数据的缓冲区所需的字符数。

### <a name="remarks"></a>备注

RFC 2045 中描述了带引号的可打印编码方案（[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）。

## <a name="uudecode"></a>UUDecode

对已 uuencode 的数据字符串进行解码，如上一次调用[UUEncode](#uuencode)。

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要解码的数据的字符串。

*nSrcLen*<br/>
*PbSrcData*的长度（以字节为单位）。

*pbDest*<br/>
调用方分配的缓冲区，用于接收已解码的数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*pbDest*的长度（以字节为单位）。 如果该函数成功，则该变量将接收写入缓冲区的字节数。 如果函数失败，则该变量将接收缓冲区的所需长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P 1003.2 b/D11 规范。

## <a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
编码字符串中的字符数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字符的已解码字符串的缓冲区所需的字节数。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P 1003.2 b/D11 规范。

## <a name="uuencode"></a>UUEncode

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

### <a name="parameters"></a>parameters

*pbSrcData*<br/>
包含要进行编码的数据的缓冲区。

*nSrcLen*<br/>
要编码的数据的长度（以字节为单位）。

*szDest*<br/>
调用方分配的缓冲区，用于接收编码数据。

*pnDestLen*<br/>
指向一个变量的指针，该变量包含*szDest*的字符长度。 如果该函数成功，则该变量将接收写入缓冲区的字符数。 如果函数失败，则变量接收缓冲区的所需长度（以字符为限）。

*lpszFile*<br/>
在*dwFlags*中指定 ATLSMTP_UUENCODE_HEADER 时要添加到标头的文件。

dwFlags<br/>
控制此函数的行为的标志。

- 将对标头进行编码 ATLSMTP_UUENCODE_HEADE。

- ATLSMTP_UUENCODE_END 最终将进行编码。

- 将执行 ATLSMTP_UUENCODE_DOT 数据堆砌。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P 1003.2 b/D11 规范。

## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength

调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>parameters

*nSrcLen*<br/>
要编码的数据的字节数。

### <a name="return-value"></a>返回值

可能包含*nSrcLen*字节编码数据的缓冲区所需的字符数。

### <a name="remarks"></a>备注

此 uuencoding 实现遵循 POSIX P 1003.2 b/D11 规范。

## <a name="see-also"></a>另请参阅

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../atl-com-desktop-components.md)
