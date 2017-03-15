---
title: "ATL 文本编码函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
caps.latest.revision: 3
translationtype: Machine Translation
ms.sourcegitcommit: 9ab4b38b2ba14aca2240d12fff966d36750a3229
ms.openlocfilehash: 86433bebe3fe84a027d7725525e028d80b67e358
ms.lasthandoff: 02/24/2017

---
# <a name="atl-text-encoding-functions"></a>ATL 文本编码函数
这些功能支持文本编码和解码。

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|调用此函数可获取十六进制数字的数值。|   
|[AtlGetVersion](#atlgetversion)|调用此函数可获取正在使用 ATL 库的版本。  |  
|[AtlHexDecode](#atlhexdecode)|对数据的以前调用已按十六进制文本中编码的字符串进行解码[AtlHexEncode](#atlhexencode)。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。|
|[AtlHexEncode](#atlhexencode)|调用此函数可将某些数据编码为十六进制文本的字符串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[AtlHexValue](#atlhexvalue)|调用此函数可获取十六进制数字的数值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|调用此函数可将 Unicode 字符串转换为 UTF-8。 |
|[BEncode](#bencode)|调用此函数可转换使用“B”编码的某些数据。|
|[BEncodeGetRequiredLength](#beencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[EscapeXML](#escapexml)|调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。|
|[GetExtendedChars](#getextendedchars)|调用此函数可获取字符串中的扩展字符的数目。|
|[IsExtendedChar](#isextendedchar)|调用此函数可了解给定字符是否为扩展字符（小于 32、大于 126，并且不是制表符、换行符或回车符）|
|[QEncode](#qencode)|调用此函数可转换使用“Q”编码的某些数据。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[QPDecode](#qpdecode)|对数据的以前调用已采用 quoted printable 格式中编码的字符串进行解码[QPEncode](#qpencode)。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。|
|[QPEncode](#qpencode)|调用此函数可对某些 Quoted Printable 格式的数据进行编码。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[取消解码](#uudecode)|对已进行 uuencode 如通过上次调用的数据的字符串进行解码[UUEncode](#uuencode)。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。|
|[UUEncode](#uuencode)|调用此函数可对某些数据进行 uuencode。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|

## <a name="requirements"></a>要求  
 **标头︰** atlenc.h  
 
## <a name="a-nameatlgethexvaluea-atlgethexvalue"></a><a name="atlgethexvalue"></a>AtlGetHexValue
调用此函数可获取十六进制数字的数值。  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>参数  
 `chIn`  
 十六进制字符"0"-"9"、 A-F 或 a-f。  
  
### <a name="return-value"></a>返回值  
 输入字符解释为十六进制数字的数值。 例如，输入"0"的返回值为 0，而 A 的输入返回值为 10。 如果输入的字符不是十六进制数字，此函数将返回-1。  
  
## <a name="a-nameatlgetversiona-atlgetversion"></a><a name="atlgetversion"></a>AtlGetVersion
调用此函数可获取正在使用 ATL 库的版本。  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>参数  
 `pReserved`  
 保留的指针。  
  
### <a name="return-value"></a>返回值  
 返回`DWORD`正在编译或执行的 ATL 库的版本的整数值。  
  
## <a name="example"></a>示例  
 应按以下方式调用的函数。  
  
 [!code-cpp[NVC_ATL_Utilities #&95;](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h  

## <a name="a-nameatlhexdecodea-atlhexdecode"></a><a name="atlhexdecode"></a>AtlHexDecode
对数据的以前调用已按十六进制文本中编码的字符串进行解码[AtlHexEncode](#atlhexencode)。  
  
```    
inline BOOL AtlHexDecode(  
   LPCSTR pSrcData,  
   int nSrcLen,  
   LPBYTE pbDest,  
   int* pnDestLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `pSrcData`  
 包含要解码的数据的字符串。  
  
 `nSrcLen`  
 以字符为单位的长度`pSrcData`。  
  
 `pbDest`  
 要接收已解码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字节为单位的长度的变量`pbDest`。 如果函数成功，该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所要求的长度以字节为单位的缓冲区。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
## <a name="a-nameatlhexdecodegetrequiredlengtha-atlhexdecodegetrequiredlength"></a><a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 已编码的字符串中的字符数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已解码的字符串的缓冲区所需的字节数`nSrcLen`字符。  
  
## <a name="a-nameatlhexencodea-atlhexencode"></a><a name="atlhexencode"></a>AtlHexEncode
调用此函数可将某些数据编码为十六进制文本的字符串。  
  
```  
inline BOOL AtlHexEncode(  
   const BYTE * pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
int * pnDestLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `pbSrcData`  
 包含要编码的数据的缓冲区。  
  
 `nSrcLen`  
 要进行编码的数据长度以字节为单位。  
  
 `szDest`  
 若要接收已编码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字符为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收缓冲区的字符所需的长度。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 源数据的每个字节编码为十六进制的 2 个字符。  
  
## <a name="a-nameatlhexencodegetrequiredlengtha-atlhexencodegetrequiredlength"></a><a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 数据进行编码的字节数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已编码的数据的缓冲区所需的字符数`nSrcLen`字节。  
  
## <a name="a-nameatlhexvaluea-atlhexvalue"></a><a name="atlhexvalue"></a>AtlHexValue
调用此函数可获取十六进制数字的数值。  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>参数  
 `chIn`  
 十六进制字符"0"-"9"、 A-F 或 a-f。  
  
### <a name="return-value"></a>返回值  
 输入字符解释为十六进制数字的数值。 例如，输入"0"的返回值为 0，而 A 的输入返回值为 10。 如果输入的字符不是十六进制数字，此函数将返回-1。  
  
## <a name="a-nameatlunicodetoutf8a-atlunicodetoutf8"></a><a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8
调用此函数可将 Unicode 字符串转换为 UTF-8。  
  
```  
ATL_NOINLINE inline int AtlUnicodeToUTF8(  
   LPCWSTR wszSrc,  
   int nSrc,  
   LPSTR szDest,  
   int nDest) throw();  
```  
  
### <a name="parameters"></a>参数  
 *wszSrc*  
 要转换的 Unicode 字符串  
  
 `nSrc`  
 以字符为单位的 Unicode 字符串的长度。  
  
 `szDest`  
 要接收已转换的字符串的调用方分配的缓冲区。  
  
 `nDest`  
 缓冲区的长度以字节为单位。  
  
### <a name="return-value"></a>返回值  
 返回已转换的字符串的字符的数。  
  
### <a name="remarks"></a>备注  
 若要确定所需的转换后的字符串缓冲区的大小，请调用此函数传递 0`szDest`和`nDest`。  
  
## <a name="a-namebencodea-bencode"></a><a name="bencode"></a>BEncode  
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
 `pbSrcData`  
 包含要编码的数据的缓冲区。  
  
 `nSrcLen`  
 要进行编码的数据长度以字节为单位。  
  
 `szDest`  
 若要接收已编码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字符为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收缓冲区的字符所需的长度。  
  
 `pszCharSet`  
 要使用用于转换的字符集。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 在 RFC 2047 中描述的"B"编码方案 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-namebeencodegetrequiredlengtha-bencodegetrequiredlength"></a><a name="beencodegetrequiredlength"></a>BEncodeGetRequiredLength 
调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 数据进行编码的字节数。  
  
 `nCharsetLen`  
 以字符为单位设置为使用用于转换的字符的长度。  
  
### <a name="return-value"></a>返回值  
 无法保存的已编码的数据的缓冲区所需的字符数`nSrcLen`字节。  
  
### <a name="remarks"></a>备注  
 在 RFC 2047 中描述的"B"编码方案 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameescapexmla-escapexml"></a><a name="escapexml"></a>EscapeXML
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
 `szIn`  
 要转换的字符串。  
  
 *nSrclen*  
 在要转换的字符串的字符长度。  
  
 *szEsc*  
 要接收已转换的字符串的调用方分配的缓冲区。  
  
 *nDestLen*  
 以字符为单位的调用方分配的缓冲区的长度。  
  
 `dwFlags`  
 描述转换的执行方式的标志。 请参阅[ATL_ESC 标志](http://msdn.microsoft.com/library/daf3aa3c-7498-4d63-9fb6-e05b4815c2b8)。  
  
### <a name="return-value"></a>返回值  
 以字符为单位转换的字符串长度。  
  
### <a name="remarks"></a>备注  
 可能的转换执行此函数的表所示︰  
  
|源|目标|  
|------------|-----------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|'|&apos;|  
|"|&quot;|  
  
## <a name="a-namegetextendedcharsa-getextendedchars"></a><a name="getextendedchars"></a>GetExtendedChars
调用此函数可获取字符串中的扩展字符的数目。  
  
```  
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `szSrc`  
 要进行分析的字符串。  
  
 `nSrcLen`  
 以字符为单位的字符串的长度。  
  
### <a name="return-value"></a>返回值  
 返回在由字符串中找到的扩展字符的数目[IsExtendedChar](#isextendedchar)。  
  
## <a name="a-nameisextendedchara-isextendedchar"></a><a name="isextendedchar"></a>IsExtendedChar
调用此函数可了解给定字符是否为扩展字符（小于 32、大于 126，并且不是制表符、换行符或回车符）  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>参数  
 *ch*  
 要进行测试的字符  
  
### <a name="return-value"></a>返回值  
 **TRUE**扩展字符，如果**FALSE**否则为。  
  
## <a name="a-nameqencodea-qencode"></a><a name="qencode"></a>QEncode
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
 `pbSrcData`  
 包含要编码的数据的缓冲区。  
  
 `nSrcLen`  
 要进行编码的数据长度以字节为单位。  
  
 `szDest`  
 若要接收已编码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字符为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收缓冲区的字符所需的长度。  
  
 `pszCharSet`  
 要使用用于转换的字符集。  
  
 *pnNumEncoded*  
 指向包含的变量在返回的不安全了要转换的字符数的指针。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 在 RFC 2047 中描述的"Q"编码方案 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameqencodegetrequiredlengtha-qencodegetrequiredlength"></a><a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength 
调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 数据进行编码的字节数。  
  
 `nCharsetLen`  
 以字符为单位设置为使用用于转换的字符的长度。  
  
### <a name="return-value"></a>返回值  
 无法保存的已编码的数据的缓冲区所需的字符数`nSrcLen`字节。  
  
### <a name="remarks"></a>备注  
 在 RFC 2047 中描述的"Q"编码方案 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt))。  
  
## <a name="a-nameqpdecodea-qpdecode"></a><a name="qpdecode"></a>QPDecode
对数据的以前调用已采用 quoted printable 格式中编码的字符串进行解码[QPEncode](#qpencode)。  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>参数  
 [in] `pbSrcData`  
 包含要解码的数据的缓冲区。  
  
 [in] `nSrcLen`  
 以字节为单位的长度`pbSrcData`。  
  
 [out] `szDest`  
 要接收已解码的数据的调用方分配的缓冲区。  
  
 [out] `pnDestLen`  
 指向包含以字节为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所要求的长度以字节为单位的缓冲区。  
  
 [in] `dwFlags`  
 描述转换的执行方式的标志。 请参阅[ATLSMTP_QPENCODE 标志](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4)。  
  
### <a name="return-value"></a>返回值  
 成功时返回 `TRUE`，失败时返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 在 RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpdecodegetrequiredlengtha-qpdecodegetrequiredlength"></a><a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 已编码的字符串中的字符数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已解码的字符串的缓冲区所需的字节数`nSrcLen`字符。  
  
### <a name="remarks"></a>备注  
 在 RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpencodea-qpencode"></a><a name="qpencode"></a>QPEncode
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
 `pbSrcData`  
 包含要编码的数据的缓冲区。  
  
 `nSrcLen`  
 要进行编码的数据长度以字节为单位。  
  
 `szDest`  
 若要接收已编码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字符为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收缓冲区的字符所需的长度。  
  
 `dwFlags`  
 描述转换的执行方式的标志。 请参阅[ATLSMTP_QPENCODE 标志](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4)。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 在 RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameqpencodegetrequiredlengtha-qpencodegetrequiredlength"></a><a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 数据进行编码的字节数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已编码的数据的缓冲区所需的字符数`nSrcLen`字节。  
  
### <a name="remarks"></a>备注  
 在 RFC 2045 中描述的 quoted printable 编码方案 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt))。  
  
## <a name="a-nameuudecodea-uudecode"></a><a name="uudecode"></a>取消解码
对已进行 uuencode 如通过上次调用的数据的字符串进行解码[UUEncode](#uuencode)。  
  
```  
inline BOOL UUDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   BYTE* pbDest,  
   int* pnDestLen) throw ();  
```  
  
### <a name="parameters"></a>参数  
 `pbSrcData`  
 包含要解码的数据的字符串。  
  
 `nSrcLen`  
 以字节为单位的长度`pbSrcData`。  
  
 `pbDest`  
 要接收已解码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字节为单位的长度的变量`pbDest`。 如果函数成功，该变量接收写入到缓冲区的字节数。 如果函数失败，该变量接收所要求的长度以字节为单位的缓冲区。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。  
  
## <a name="a-nameuudecodegetrequiredlengtha-uudecodegetrequiredlength"></a><a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 已编码的字符串中的字符数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已解码的字符串的缓冲区所需的字节数`nSrcLen`字符。  
  
### <a name="remarks"></a>备注  
 此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。  
  
## <a name="a-nameuuencodea-uuencode"></a><a name="uuencode"></a>UUEncode
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
 `pbSrcData`  
 包含要编码的数据的缓冲区。  
  
 `nSrcLen`  
 要进行编码的数据长度以字节为单位。  
  
 `szDest`  
 若要接收已编码的数据的调用方分配的缓冲区。  
  
 `pnDestLen`  
 指向包含以字符为单位的长度的变量`szDest`。 如果函数成功，该变量接收写入到缓冲区的字符数。 如果函数失败，该变量接收缓冲区的字符所需的长度。  
  
 *lpszFile*  
 要在中指定了 ATLSMTP_UUENCODE_HEADER 标头中添加的文件`dwFlags`。  
  
 `dwFlags`  
 控制此函数的行为的标志。 请参阅[ATLSMTP_UUENCODE 标志](http://msdn.microsoft.com/library/ecb79b81-b764-4a48-a05c-a9dee6e7bbce)。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。  
  
## <a name="a-nameuuencodegetrequiredlengtha-uuencodegetrequiredlength"></a><a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength
调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>参数  
 `nSrcLen`  
 数据进行编码的字节数。  
  
### <a name="return-value"></a>返回值  
 无法保存的已编码的数据的缓冲区所需的字符数`nSrcLen`字节。  
  
### <a name="remarks"></a>备注  
 此 uuencoding 实现遵循 POSIX P1003.2b/D11 规范。  
  
### <a name="see-also"></a>另请参阅  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)   
