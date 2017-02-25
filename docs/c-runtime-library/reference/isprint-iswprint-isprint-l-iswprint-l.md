---
title: "isprint、iswprint、_isprint_l、_iswprint_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswprint"
  - "isprint"
  - "_isprint_l"
  - "_iswprint_l"
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
  - "iswprint"
  - "_istprint"
  - "isprint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isprint_l 函数"
  - "_istprint 函数"
  - "_iswprint_l 函数"
  - "isprint 函数"
  - "isprint_l 函数"
  - "istprint 函数"
  - "iswprint 函数"
  - "iswprint_l 函数"
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# isprint、iswprint、_isprint_l、_iswprint_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示可打印字符。  
  
## 语法  
  
```  
int isprint(  
   int c   
);  
int iswprint(  
   wint_t c   
);  
int _isprint_l(  
   int c,  
   _locale_t locale  
);  
int _iswprint_l(  
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
 如果 `c` 是可打印字母的特定表示，则每个实例返回非零值。  如果 `c` 可打印字符包含空格 \(0x20 – 0x7E\)，`isprint` 返回一个非零值。  如果 `c` 可打印字符包含空格的宽字符，`iswprint` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 函数的测试条件的结果依赖区域设置的`LC_CTYPE` 类别设置；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  这些不带 `_l` 后缀的函数版本对任何区域设置相关行为使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传入的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果`c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），`isprint`和`_isprint_l`的行为是未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_** `istprint`|`isprint`|[\_ismbcprint](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswprint`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isprint`|\<ctype.h\>|  
|`iswprint`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isprint_l`|\<ctype.h\>|  
|`_iswprint_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)