---
title: "c16rtomb c32rtomb1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "c16rtomb"
  - "c32rtomb"
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
  - "c16rtomb"
  - "c32rtomb"
  - "uchar/c16rtomb"
  - "uchar/c32rtomb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "c16rtomb 函数"
  - "c32rtomb 函数"
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# c16rtomb, c32rtomb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在当前区域设置中将 UTF\-16 或 UTF\-32 宽字符转换为多字节字符。  
  
## 语法  
  
```  
size_t c16rtomb(  
    char *mbchar,   
    char16_t wchar,  
    mbstate_t *state  
);  
size_t c32rtomb(  
    char *mbchar,   
    char32_t wchar,  
    mbstate_t *state  
);  
```  
  
#### 参数  
 \[out\] `mbchar`  
 指向用于存储转换后的多字节字符的数组的指针。  
  
 \[in\] `wchar`  
 要转换的宽字符。  
  
 \[in, out\] `state`  
 指向 `mbstate_t` 对象的指针。  
  
## 返回值  
 数组对象中存储的字节数 `mbchar` 包括任何位移序列。 如果 `wchar` 不是有效的宽字符，则将返回 \(`size_t`\)\(\-1\) 值，`errno` 被设置为 `EILSEQ`，`state` 的值未指定。  
  
## 备注  
 `c16rtomb` 函数在当前区域设置中将 UTF\-16 字符 `wchar` 转换为等效多字节窄字符序列。 如果 `mbchar` 不是 null 指针，函数会在 `mbchar` 指向的数组对象中存储转换后的序列。`mbchar` 中最多可存储 `MB_CUR_MAX` 个字节，`state` 被设置为生成的多字节位移状态。    如果 `wchar` 是 null 宽字符，则会存储还原初始位移状态所需的序列，如果需要，后面跟 null 字符，并将 `state` 设置为初始转换状态。`c32rtomb` 函数完全相同，但它转换的是 UTF\-32 字符。  
  
 如果 `mbchar` 是 null 指针，该行为对于 `mbchar` 相当于调用替换内部缓冲区的函数，对于 `wchar` 相当于宽 null 字符。  
  
 `state` 转换状态对象让你可以后续调用此函数和维持多字节输出字符的位移状态的其他可重启函数。 如果混合使用可重启和非可重启函数，或者如果在可重启函数调用之间调用 `setlocale`，结果不确定。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`c16rtomb`, `c32rtomb`|C, C\+\+: \<uchar.h\>|  
  
 有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtoc16, mbrtoc32](../../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)