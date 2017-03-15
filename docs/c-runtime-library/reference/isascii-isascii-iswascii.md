---
title: "isascii，__isascii、 iswascii | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswascii"
  - "__isascii"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "iswascii"
  - "istascii"
  - "__isascii"
  - "_istascii"
  - "isascii"
  - "ctype/isascii"
  - "ctype/__isascii"
  - "corecrt_wctype/iswascii"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__isascii 函数"
  - "_isascii 函数"
  - "isascii 函数"
  - "_istascii 函数"
  - "istascii 函数"
  - "iswascii 函数"
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# isascii，__isascii、 iswascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定特定字符是否是 ASCII 字符。  
  
## 语法  
  
```  
int __isascii(   
   int c   
);  
int iswascii(   
   wint_t c   
);  
#define isascii __isascii  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
## 返回值  
 如果 `c` 是 ASCII 字符的特定表示形式，则每个实例将返回非零值。 如果 `__isascii` 是 ASCII 字符（位于范围 0x00 – 0x7F 中），则 `c` 将返回非零值。 如果 `iswascii` 是 ASCII 字符的宽字符表示形式，则 `c` 将返回一个非零值。 如果 `c` 不满足测试条件，则这些例程都返回 0。  
  
## 备注  
 同时 `__isascii` 和 `iswascii` 作为宏实现，除非定义预处理器宏 \_CTYPE\_DISABLE\_MACROS。  
  
 为了向后兼容 `isascii` 作为宏才实现 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定义或定义为 0; 否则是不确定。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isascii`, `__isascii`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
|`iswascii`|C: \< wctype.h \>，\< ctype.h \> 或 \< wchar.h \><br /><br /> C \+ \+: \< cwctype \>，\< cctype \>，\< wctype.h \>，\< ctype.h \> 或 \< wchar.h \>|  
  
 `isascii`, ，`__isascii` 和 `iswascii` 函数是 Microsoft 专用。 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)