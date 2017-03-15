---
title: "数据类型常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FLT_MIN"
  - "SHRT_MAX"
  - "CHAR_MIN"
  - "MB_LEN_MAX"
  - "DBL_EPSILON"
  - "SHRT_MIN"
  - "_FLT_RADIX"
  - "FLT_DIG"
  - "FLT_MAX_10_EXP"
  - "FLT_MANT_DIG"
  - "DBL_MAX_EXP"
  - "SCHAR_MIN"
  - "SCHAR_MAX"
  - "DBL_MIN"
  - "FLT_MIN_10_EXP"
  - "_DBL_ROUNDS"
  - "USHRT_MAX"
  - "FLT_MAX_EXP"
  - "LONG_MAX"
  - "DBL_MAX"
  - "DBL_DIG"
  - "FLT_MIN_EXP"
  - "INT_MIN"
  - "DBL_MIN_10_EXP"
  - "CHAR_BIT"
  - "INT_MAX"
  - "ULONG_MAX"
  - "DBL_MIN_EXP"
  - "LONG_MIN"
  - "_FLT_ROUNDS"
  - "DBL_MANT_DIG"
  - "_DBL_RADIX"
  - "CHAR_MAX"
  - "FLT_MAX"
  - "DBL_MAX_10_EXP"
  - "UCHAR_MAX"
  - "FLT_EPSILON"
  - "UINT_MAX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DBL_RADIX 常量"
  - "_DBL_ROUNDS 常量"
  - "_FLT_RADIX 常量"
  - "_FLT_ROUNDS 常量"
  - "CHAR_BIT 常量"
  - "CHAR_MAX 常量"
  - "CHAR_MIN 常量"
  - "常量 [C++], 数据类型"
  - "数据类型常量 [C++]"
  - "DBL_DIG 常量"
  - "DBL_EPSILON 常量"
  - "DBL_MANT_DIG 常量"
  - "DBL_MAX 常量"
  - "DBL_MAX_10_EXP 常量"
  - "DBL_MAX_EXP 常量"
  - "DBL_MIN 常量"
  - "DBL_MIN_10_EXP 常量"
  - "DBL_MIN_EXP 常量"
  - "DBL_RADIX 常量"
  - "DBL_ROUNDS 常量"
  - "FLT_DIG 常量"
  - "FLT_EPSILON 常量"
  - "FLT_MANT_DIG 常量"
  - "FLT_MAX 常量"
  - "FLT_MAX_10_EXP 常量"
  - "FLT_MAX_EXP 常量"
  - "FLT_MIN 常量"
  - "FLT_MIN_10_EXP 常量"
  - "FLT_MIN_EXP 常量"
  - "FLT_RADIX 常量"
  - "FLT_ROUNDS 常量"
  - "INT_MAX 常量"
  - "INT_MIN 常量"
  - "LONG_MAX 常量"
  - "LONG_MIN 常量"
  - "MB_LEN_MAX 常量"
  - "SCHAR_MAX 常量"
  - "SCHAR_MIN 常量"
  - "SHRT_MAX 常量"
  - "SHRT_MIN 常量"
  - "UCHAR_MAX 常量"
  - "UINT_MAX 常量"
  - "ULONG_MAX 常量"
  - "USHRT_MAX 常量"
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数据类型常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常数数据类型是整数数据类型允许值的实现依赖范围。  下面列出的常数在 LIMITS.H. 为整型数据类型的范围和定义。  
  
> [!NOTE]
>  \/J 编译器选项将默认值从`char` 类型`unsigned`.  
  
|常量|值|含义|  
|--------|-------|--------|  
|**SCHAR\_MAX**|127|最大值签名的 `char` 值|  
|**SCHAR\_MIN**|–128|最小数量签名的 `char` 值|  
|**UCHAR\_MAX**|255 \(0xff\)|最大`unsigned char` 值|  
|**CHAR\_BIT**|8|在 `char`中的位数|  
|**USHRT\_MAX**|65535 \(0xffff\)|最大值 **unsigned short**|  
|**SHRT\_MAX**|32767|最大 \(有符号的\) **short** 值|  
|**SHRT\_MIN**|–32768|最小 \(有符号的\) **short** 值|  
|**UINT\_MAX**|4294967295 \(0xffffffff\)|最大 `unsigned int` 值|  
|**ULONG\_MAX**|4294967295 \(0xffffffff\)|最大 `unsigned long` 值|  
|**INT\_MAX**|2147483647|最大值（有符号） `int` 值|  
|**INT\_MIN**|–2147483647–1|最小（有符号） `int` 值|  
|**LONG\_MAX**|2147483647|最大 \(有符号的\) **long** 值|  
|**LONG\_MIN**|–2147483647–1|最小 \(有符号的\) **long** 值|  
|**CHAR\_MAX**|127 \(255 if \/J option used\)|最大 `char` 值|  
|**CHAR\_MIN**|–128 \(0 if \/J option used\)|最小 `char` 值|  
|**MB\_LEN\_MAX**|2|最大字节数 `char`的多字节|  
|**\_I64\_MAX**|9223372036854775807|最大 \(有符号的\)**int64** 值|  
|**\_I64\_MIN**|\-9223372036854775807\-1|最小 \(有符号的\)**int64** 值|  
|**\_UI64\_MAX**|0xffffffffffffffff|最大（无符号） \_\_**int64** 值|  
  
 下列常数在 FLOAT.H 给定范围以及 **双倍行距** 和\/或 **浮动** 数据类型的其他特性和定义：  
  
|常量|值|说明|  
|--------|-------|--------|  
|**DBL\_DIG**|15|\# 精度十进制|  
|**DBL\_EPSILON**|2.2204460492503131e\-016|最小 1.0\+ 此**DBL\_EPSILON**不等于1.0|  
|**DBL\_MANT\_DIG**|53|\# 在尾数的位|  
|**DBL\_MAX**|1.7976931348623158e\+308|最大值|  
|**DBL\_MAX\_10\_EXP**|308|指数最大十进制|  
|**DBL\_MAX\_EXP**|1024|指数最大二进制|  
|**DBL\_MIN**|2.2250738585072014e\-308|最小正值。|  
|**DBL\_MIN\_10\_EXP**|\(\-307\)|指数最小十进制|  
|**DBL\_MIN\_EXP**|\(–1021\)|指数最小的二进制文件|  
|**\_DBL\_RADIX**|2|指数基数|  
|**\_DBL\_ROUNDS**|1|添加舍入：在附近|  
|**FLT\_DIG**|6|小数位数的精度。|  
|**FLT\_EPSILON**|1.192092896e\-07F|最小 1.0\+**FLT\_EPSILON** 不等于1.0|  
|**FLT\_MANT\_DIG**|24|尾数位的数目|  
|**FLT\_MAX**|3.402823466e\+38F|最大值|  
|**FLT\_MAX\_10\_EXP**|38|指数最大十进制|  
|**FLT\_MAX\_EXP**|128|指数最大二进制|  
|**FLT\_MIN**|1.175494351e\-38F|最小正值。|  
|**FLT\_MIN\_10\_EXP**|\(–37\)|指数最小十进制|  
|**FLT\_MIN\_EXP**|\(–125\)|指数最小的二进制文件|  
|**FLT\_RADIX**|2|指数基数|  
|**FLT\_ROUNDS**|1|添加舍入：在附近|  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)