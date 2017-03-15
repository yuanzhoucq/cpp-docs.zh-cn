---
title: "isspace、iswspace、_isspace_l、_iswspace_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswspace"
  - "_isspace_l"
  - "_iswspace_l"
  - "isspace"
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
  - "iswspace"
  - "_istspace"
  - "isspace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isspace_l 函数"
  - "_istspace 函数"
  - "_iswspace_l 函数"
  - "isspace 函数"
  - "isspace_l 函数"
  - "istspace 函数"
  - "iswspace 函数"
  - "iswspace_l 函数"
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# isspace、iswspace、_isspace_l、_iswspace_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示空白字符。  
  
## 语法  
  
```  
int isspace(  
   int c   
);  
int iswspace(  
   wint_t c   
);  
int _isspace_l(  
   int c,  
   _locale_t locale  
);  
int _iswspace_l(  
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
 如果 `c` 是空格字符的特定表示，则每个实例返回非零值。  如果 `c` 是空格字符\(0x09 – 0x0D or 0x20\)，则 `isspace` 返回一个非零值。  `isspace` 函数测试条件的结果依赖区域设置的 `LC_CTYPE` 类别设置；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数版本对任何区域设置相关行为使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传入的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `c` 是对应于标准空格字符的宽字符，则`iswspace` 返回一个非零值。  
  
 如果 `c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），则`isspace` 和 `_isspace_l` 行为未定义的。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_** `istspace`|`isspace`|[\_ismbcspace](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswspace`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isspace`|\<ctype.h\>|  
|`iswspace`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isspace_l`|\<ctype.h\>|  
|`_iswspace_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)