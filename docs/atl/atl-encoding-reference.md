---
title: "ATL 编码引用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2a97809fefdc0a5e6e7d90e7b62bbee83f28bfb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-encoding-reference"></a>ATL 编码引用
在常见的 Internet 标准，如进行 uuencode 十六进制、 范围和 UTF8 编码支持在 atlenc.h 中找到的代码。  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|调用此函数可获取十六进制数字的数值。|  
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|对数据的以前调用已按十六进制文本，如中编码的字符串进行解码[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)。|  
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的十六进制编码字符串解码而来的数据。|  
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|调用此函数可将某些数据编码为十六进制文本的字符串。|  
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|  
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|调用此函数可将 Unicode 字符串转换为 UTF-8。|  
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|调用此函数可转换使用“B”编码的某些数据。|  
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|  
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|调用此函数可将无法在 XML 中安全使用的字符转换为其安全的等效字符。|  
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|调用此函数可获取字符串中的扩展字符的数目。|  
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|调用此函数可了解给定字符是否为扩展字符（小于 32、大于 126，并且不是制表符、换行符或回车符）|  
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|调用此函数可转换使用“Q”编码的某些数据。|  
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|  
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|对已采用 quoted printable 格式进行编码到的以前调用的数据的字符串进行解码[QPEncode](reference/atl-text-encoding-functions.md#qpencode)。|  
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的 Quoted Printable 编码字符串解码而来的数据。|  
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|调用此函数可对某些 Quoted Printable 格式的数据进行编码。|  
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|  
|[取消解码](reference/atl-text-encoding-functions.md#uudecode)|对已进行 uuencode 如通过上次调用的数据的字符串进行解码[进行 UUEncode](reference/atl-text-encoding-functions.md#uuencode)。|  
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字节为单位），该缓冲区可包含从指定长度的已进行 uuencode 的字符串解码而来的数据。|  
|[进行 UUEncode](reference/atl-text-encoding-functions.md#uuencode)|调用此函数可对某些数据进行 uuencode。|  
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|调用此函数可获取某个缓冲区的大小（以字符为单位），该缓冲区可包含从指定大小的数据编码而来的字符串。|  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../atl/atl-com-desktop-components.md)

