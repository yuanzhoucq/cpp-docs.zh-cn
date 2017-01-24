---
title: "从带符号的整型转换 | Microsoft Docs"
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
  - "转换 [C++], 整数"
  - "数据类型转换 [C++], 有符号和无符号整数"
  - "整数, 转换"
  - "整数转换, 从有符号"
  - "类型转换 [C++], 有符号和无符号整数"
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从带符号的整型转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当一个带符号整数转换为一个具有相等或更大大小的无符号整数且该带符号整数的值不为负时，值保持不变。  转换是通过对带符号整数进行符号扩展来实现的。  通过截断高位将带符号整数转换为较短的带符号整数。  结果被解释为无符号值，如此示例中所示。  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 在将带符号整数转换为浮点值时，不会丢失信息，只不过在将 **long int** 或 **unsigned long int** 值转换为 **float** 值时，可能会丢失某些精度。  
  
 下表汇总了来自带符号整型的转换。  此表假定默认情况下 `char` 类型是带符号的。  如果使用编译时选项将 `char` 类型的默认值更改为无符号，则应用 `unsigned char` 类型的[从无符号整型转换](../c-language/conversions-from-unsigned-integral-types.md)表中给定的转换，而不是应用“从带符号整型转换”表中给定的转换。  
  
### 从带符号整型的转换  
  
|从|到|方法|  
|-------|-------|--------|  
|`char`1|**short**|符号扩展|  
|`char`|**long**|符号扩展|  
|`char`|`unsigned char`|保留模式；高序位失去符号位的函数|  
|`char`|**unsigned short**|符号扩展至 **short**；将 **short** 转换为 **unsigned short**|  
|`char`|`unsigned long`|符号扩展至 **long**；将 **long** 转换为 `unsigned long`|  
|`char`|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|  
|`char`|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|  
|`char`|`long double`|符号扩展至 **long**；将 **long** 转换为 **double**|  
|**short**|`char`|保留低位字节|  
|**short**|**long**|符号扩展|  
|**short**|`unsigned char`|保留低位字节|  
|**short**|**unsigned short**|保留位模式；高序位丢失符号位的函数|  
|**short**|`unsigned long`|符号扩展至 **long**；将 **long** 转换为 `unsigned long`|  
|**short**|**float**|符号扩展至 **long**；将 **long** 转换为 **float**|  
|**short**|**double**|符号扩展至 **long**；将 **long** 转换为 **double**|  
|**short**|`long double`|符号扩展至 **long**；将 **long** 转换为 **double**|  
|**long**|`char`|保留低位字节|  
|**long**|**short**|保留低位字|  
|**long**|`unsigned char`|保留低位字节|  
|**long**|**unsigned short**|保留低位字|  
|**long**|`unsigned long`|保留位模式；高序位丢失符号位的函数|  
|**long**|**float**|表示为 **float**。  如果 **long** 不能精确表示，则某些精度将丢失。|  
|**long**|**double**|表示为 **double**。  如果 **long** 不能精确表示为 **double**，则某些精度将丢失。|  
|**long**|`long double`|表示为 **double**。  如果 **long** 不能精确表示为 **double**，则某些精度将丢失。|  
  
 1.  所有 `char` 项假定默认情况下 `char` 类型是有符号的。  
  
 **Microsoft 专用**  
  
 对于 Microsoft 32 位 C 编译器，整数与 **long** 等效。  `int` 值的转换与 **long** 的相同。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [赋值转换](../c-language/assignment-conversions.md)