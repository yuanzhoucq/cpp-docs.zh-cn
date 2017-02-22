---
title: "ATL 编码引用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "编码"
  - "编码, 函数"
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ATL 编码引用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常规Internet标准大小的编码例如uuencode、十六进制和UTF8由atlenc.h找到的代码支持。  
  
### 函数  
  
|||  
|-|-|  
|[AtlGetHexValue](../Topic/AtlGetHexValue.md)|调用此函数获取一个十六进制数字的数值。|  
|[AtlHexDecode](../Topic/AtlHexDecode.md)|解密已输入为十六进制文本\(如以前调用了 [AtlHexEncode](../Topic/AtlHexEncode.md)数据的字符串。|  
|[AtlHexDecodeGetRequiredLength](../Topic/AtlHexDecodeGetRequiredLength.md)|调用此函数获取范围中可以包含从指定长度的一个十六进制编码字符串解码的数据缓冲区的字节。|  
|[AtlHexEncode](../Topic/AtlHexEncode.md)|调用此函数的进入某些数据作为十六进制文本字符串。|  
|[AtlHexEncodeGetRequiredLength](../Topic/AtlHexEncodeGetRequiredLength.md)|调用此函数获取在可以包含从指定的范围的数据输入的字符串缓冲区的字符范围。|  
|[AtlUnicodeToUTF8](../Topic/AtlUnicodeToUTF8.md)|调用此函数将Unicode字符串转换为UTF\-8。|  
|[BEncode](../Topic/BEncode.md)|使用“B”编码，调用此函数将一些数据。|  
|[BEncodeGetRequiredLength](../Topic/BEncodeGetRequiredLength.md)|调用此函数获取在可以包含从指定的范围的数据输入的字符串缓冲区的字符范围。|  
|[EscapeXML](../Topic/EscapeXML.md)|调用此函数是不安全的用于XML对这些安全的等效字符。|  
|[GetExtendedChars](../Topic/GetExtendedChars.md)|调用此函数获取外接字符串中的字符数。|  
|[IsExtendedChar](../Topic/IsExtendedChar.md)|调用此函数查看，如果特定字符是一个扩展字符\(小于32，大于126，而不是选项、换行符或回车\)|  
|[QEncode](../Topic/QEncode.md)|使用“Q”编码，调用此函数将一些数据。|  
|[QEncodeGetRequiredLength](../Topic/QEncodeGetRequiredLength.md)|调用此函数获取在可以包含从指定的范围的数据输入的字符串缓冲区的字符范围。|  
|[QPDecode](../Topic/QPDecode.md)|解密已输入了以引用可打印的格式\(如以前调用了 [QPEncode](../Topic/QPEncode.md)数据的字符串。|  
|[QPDecodeGetRequiredLength](../Topic/QPDecodeGetRequiredLength.md)|调用此函数获取范围中可以包含从指定长度的引用可打印编码字符串解码的数据缓冲区的字节。|  
|[QPEncode](../Topic/QPEncode.md)|调用此函数的进入某些数据以引用可打印的格式。|  
|[QPEncodeGetRequiredLength](../Topic/QPEncodeGetRequiredLength.md)|调用此函数获取在可以包含从指定的范围的数据输入的字符串缓冲区的字符范围。|  
|[UUDecode](../Topic/UUDecode.md)|解密uuencoded例如以前调用了 [UUEncode](../Topic/UUEncode.md)数据的字符串。|  
|[UUDecodeGetRequiredLength](../Topic/UUDecodeGetRequiredLength.md)|调用此函数获取范围中可以包含从指定长度的一个uuencoded字符串解码的数据缓冲区的字节。|  
|[UUEncode](../Topic/UUEncode.md)|调用该功能。uuencode某些数据。|  
|[UUEncodeGetRequiredLength](../Topic/UUEncodeGetRequiredLength.md)|调用此函数获取在可以包含从指定的范围的数据输入的字符串缓冲区的字符范围。|  
  
### 宏  
  
|||  
|-|-|  
|[ATL\_ESC标志](../Topic/ATL_ESC%20Flags.md)|这些标志用于控件 [EscapeXML](../Topic/EscapeXML.md)行为。|  
|[ATLSMTP\_QPENCODE标志](../Topic/ATLSMTP_QPENCODE%20Flags.md)|这些标志描述引用可打印的编码如何将由 [QPEncode](../Topic/QPEncode.md)执行。|  
|[ATLSMTP\_UUENCODE标志](../Topic/ATLSMTP_UUENCODE%20Flags.md)|这些标志描述uuencoding如何将由 [UUEncode](../Topic/UUEncode.md)执行。|  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)