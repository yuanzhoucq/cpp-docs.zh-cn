---
title: "C++ 整数限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "整数限制"
  - "限制, integer"
  - "限制, 整数常量"
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 整数限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 下表列出了整数类型的限制。  这些限制在标准标头文件 LIMITS.H 中定义。  Microsoft C 还允许声明固定大小的整数变量，即大小为 8 位、16 位、或 32 位的整数类型。  有关固定大小整数的详细信息，请参阅[固定大小整数类型](../c-language/c-sized-integer-types.md)。  
  
### 对整数常量的限制  
  
|**常量**|含义|值|  
|------------|--------|-------|  
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
|**INT\_MIN**|`int` 类型的变量的最小值。|–2147483647 – 1|  
|**INT\_MAX**|`int` 类型的变量的最大值。|2147483647|  
|**UINT\_MAX**|`unsigned int` 类型的变量的最大值。|4294967295 \(0xffffffff\)|  
|**LONG\_MIN**|**long** 类型的变量的最小值。|–2147483647 – 1|  
|**LONG\_MAX**|**long** 类型的变量的最大值。|2147483647|  
|**ULONG\_MAX**|`unsigned long` 类型的变量的最大值。|4294967295 \(0xffffffff\)|  
  
 如果值超出了最大整数表示形式，则 Microsoft 编译器会产生错误。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C 整数常量](../c-language/c-integer-constants.md)