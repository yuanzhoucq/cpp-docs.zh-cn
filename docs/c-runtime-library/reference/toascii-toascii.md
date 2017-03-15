---
title: "toascii __toascii | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__toascii"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__toascii"
  - "toascii"
  - "ctype/toascii"
  - "ctype/__toascii"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toascii 函数"
  - "字符串转换为 ASCII 字符"
  - "__toascii 函数"
  - "ASCII 字符，将转换为"
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# toascii __toascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符转换为 7 位 ASCII 中，通过截断。  
  
## 语法  
  
```  
int __toascii(  
   int c   
);  
#define toascii __toascii  
```  
  
#### 参数  
 `c`  
 要转换的字符。  
  
## 返回值  
 `__toascii` 将的值转换 `c` 到 7 位 ASCII 范围，并返回结果。 保留以指示错误是没有返回值。  
  
## 备注  
 `__toascii` 例程通过截断为低序位 7 位将给定的字符转换为 ASCII 字符。 应用无其他转换。  
  
 `__toascii` 例程定义为宏，除非定义预处理器宏 \_CTYPE\_DISABLE\_MACROS。 为了向后兼容 `toascii` 定义为宏时，才 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定义或定义为 0; 否则是不确定。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`toascii`, `__toascii`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
  
 `toascii` 宏是扩展名为 POSIX，和 `__toascii` 是 POSIX 扩展的 Microsoft 专用实现。 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)   
 [to 函数](../../c-runtime-library/to-functions.md)