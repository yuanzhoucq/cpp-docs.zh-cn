---
title: ATL 编码引用
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: a9c7689e49efce0d65e945f1a032a680e2277594
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375867"
---
# <a name="atl-encoding-reference"></a>ATL 编码引用

在 atlenc 中找到的代码支持使用各种常见 Internet 标准 (如 uuencode、十六进制和 UTF8) 进行编码。

### <a name="functions"></a>函数

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|调用此函数可获取十六进制数字的数值。|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|对已编码为十六进制文本的数据字符串进行解码, 如上一次对[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)的调用。|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|调用此函数可将某些数据编码为十六进制文本的字符串。|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|调用此函数可将 Unicode 字符串转换为 UTF-8。|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|调用此函数可转换使用“B”编码的某些数据。|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|调用此函数可获取字符串中的扩展字符的数目。|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|调用此函数可查明给定字符是否是扩展字符 (小于 32, 大于 126, 而不是制表符、换行符或回车符)|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|调用此函数可转换使用“Q”编码的某些数据。|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|对已使用带引号的可打印格式进行编码的数据字符串进行解码, 如以前对[QPEncode](reference/atl-text-encoding-functions.md#qpencode)的调用。|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。|
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|调用此函数可对某些 Quoted Printable 格式的数据进行编码。|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|对已 uuencode 的数据字符串进行解码, 如上一次调用[UUEncode](reference/atl-text-encoding-functions.md#uuencode)。|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。|
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|调用此函数可对某些数据进行 uuencode。|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)
