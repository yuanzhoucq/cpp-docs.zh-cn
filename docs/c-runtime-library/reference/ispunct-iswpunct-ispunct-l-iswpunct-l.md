---
title: "ispunct、iswpunct、_ispunct_l、_iswpunct_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ispunct"
  - "_iswpunct_l"
  - "iswpunct"
  - "_ispunct_l"
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
  - "iswpunct"
  - "_istpunct"
  - "ispunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ispunct_l 函数"
  - "_istpunct 函数"
  - "_iswpunct_l 函数"
  - "ispunct 函数"
  - "ispunct_l 函数"
  - "istpunct 函数"
  - "iswpunct 函数"
  - "iswpunct_l 函数"
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# ispunct、iswpunct、_ispunct_l、_iswpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示标点符号字符。  
  
## 语法  
  
```  
int ispunct(  
   int c   
);  
int iswpunct(  
   wint_t c   
);  
int _ispunct_l(  
   int c,  
   _locale_t locale  
);  
int _iswpunct_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `c` 是一个标点符号字符的特定表示，则每个程序返回非零值。  对于所有可打印字符`ispunct` 返回非零值，它不是空格字符也不是对于 `isalnum` 是非零的字符。  对于所有可打印的宽字符`iswpunct` 返回非零值，它既不是空格宽字符也不是对于 `iswalnum` 是非零的宽字符 。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 关于`ispunct` 函数测试条件的结果依赖区域设置的 `LC_CTYPE`类别设置；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数版本对任何区域设置相关行为使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传入的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`ispunct`和`_ispunct_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_** `istpunct`|`ispunct`|[\_ismbcpunct](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswpunct`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ispunct`|\<ctype.h\>|  
|`iswpunct`|\<ctype.h\> 或 \<wchar.h\>|  
|`_ispunct_l`|\<ctype.h\>|  
|`_iswpunct_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)