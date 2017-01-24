---
title: "整数限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "整数限制"
  - "整数限制"
  - "限制, integer"
  - "LIMITS.H 头文件"
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 整数限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 下表列出了整数类型的限制。  标准头文件 LIMITS.H 中也定义了这些限制。  
  
### 对整数常量的限制  
  
|常量|含义|值|  
|--------|--------|-------|  
|**CHAR\_BIT**|不是位域的最小变量中的位数。|8|  
|**SCHAR\_MIN**|**signed char** 类型的变量的最小值。|–128|  
|**SCHAR\_MAX**|**signed char** 类型的变量的最大值。|127|  
|**UCHAR\_MAX**|`unsigned char` 类型的变量的最大值。|255 \(0xff\)|  
|**CHAR\_MIN**|`char` 类型的变量的最小值。|–128；如果使用了 \/J 选项，则为 0|  
|**CHAR\_MAX**|`char` 类型的变量的最大值。|127；如果使用了 \/J 选项，则为 255|  
|**MB\_LEN\_MAX**|多字符常量中的最大字节数。|5|  
|**SHRT\_MIN**|**short** 类型的变量的最小值。|–32768|  
|**SHRT\_MAX**|**short** 类型的变量的最大值。|32767|  
|**USHRT\_MAX**|**unsigned short** 类型的变量的最大值。|65535 \(0xffff\)|  
|**INT\_MIN**|`int` 类型的变量的最小值。|–2147483648|  
|**INT\_MAX**|`int` 类型的变量的最大值。|2147483647|  
|**UINT\_MAX**|`unsigned int` 类型的变量的最大值。|4294967295 \(0xffffffff\)|  
|**LONG\_MIN**|**long** 类型的变量的最小值。|–2147483648|  
|**LONG\_MAX**|**long** 类型的变量的最大值。|2147483647|  
|**ULONG\_MAX**|`unsigned long` 类型的变量的最大值。|4294967295 \(0xffffffff\)|  
|**\_I64\_MIN**|`__int64` 类型的变量的最小值|\-9223372036854775808|  
|**\_I64\_MAX**|`__int64` 类型的变量的最大值|9223372036854775807|  
|**\_UI64\_MAX**|**unsigned \_\_int64** 类型的变量的最大值|18446744073709551615 \(0xffffffffffffffff\)|  
  
 如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [浮点限制](../cpp/floating-limits.md)