---
title: "isgraph、iswgraph、_isgraph_l、_iswgraph_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "isgraph"
  - "iswgraph"
  - "_iswgraph_l"
  - "_isgraph_l"
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
  - "_isgraph_l"
  - "_iswgraph_l"
  - "_ismbcgraph_l"
  - "Isgraph"
  - "_istgraph_l"
  - "_istgraph"
  - "iswgraph"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isgraph_l 函数"
  - "_ismbcgraph_l 函数"
  - "_istgraph 函数"
  - "_istgraph_l 函数"
  - "_iswgraph_l 函数"
  - "isgraph 函数"
  - "istgraph 函数"
  - "iswgraph 函数"
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isgraph、iswgraph、_isgraph_l、_iswgraph_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示图形字符。  
  
## 语法  
  
```  
int isgraph(  
   int c   
);  
int iswgraph(  
   wint_t c   
);  
int _isgraph_l(  
   int c,  
   _locale_t locale  
);  
int _iswgraph_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `c`  
 要测试的整数。  
  
## 返回值  
 如果 `c` 是可打印字母的特定表示，则每个实例返回非零值。  除空格外，如果 `c` 是可打印字符，`isgraph` 返回一个非零值。  除了一个宽字符空间以外，如果 `c` 是可打印的宽字符`iswgraph` 返回一个非零值。  如果 `c` 不满足测试条件，则每个实例都返回0。  
  
 这些带有 `_l` 后缀的函数的版本使用传递的区域设置，而不是与区域设置行为相关的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `isgraph`和`_isgraph_l` 的行为是未定义的，如果  `c`不是 EOF 或在 0 到 0xFF范围（包含 0 和 0xFF）.  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istgraph`|`isgraph`|[\_ismbcgraph](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswgraph`|  
|`_istgraph_l`|`_isgraph_l`|[\_ismbcgraph\_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswgraph_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isgraph`|\<ctype.h\>|  
|`iswgraph`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isgraph_l`|\<ctype.h\>|  
|`_iswgraph_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)