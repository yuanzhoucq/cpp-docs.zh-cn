---
title: "isblank、iswblank、_isblank_l、_iswblank_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "isblank"
  - "_isblank_l"
  - "iswblank"
  - "_iswblank_l"
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
  - "_iswblank_l"
  - "isblank"
  - "_istblank_l"
  - "_istblank"
  - "_isblank_l"
  - "iswblank"
dev_langs: 
  - "C++"
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# isblank、iswblank、_isblank_l、_iswblank_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示空白字符。  
  
## 语法  
  
```  
int isblank(  
   int c   
);  
int iswblank(  
   wint_t c   
);  
int _isblank_l(  
   int c,  
   _locale_t locale  
);  
int _iswblank_l(  
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
 如果 `c` 是空格或水平选项卡字符的特殊表示形式，或是用于分隔文本行内的单词的特定于区域设置的集之一，则这些例程返回非零。  如果 `c` 是空格字符 \(0x20\) 或水平选项卡字符 \(0x09\)，则 `isblank` 返回一个非零值。  `isblank` 函数的测试条件的结果依赖区域设置的 `LC_CTYPE` 类别设置；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数版本对任何区域设置相关行为使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传入的区域设置。  有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `c` 是对应于标准空格或水平制表符的宽位字符，则`iswblank` 返回一个非零值。  
  
 如果 `c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），则 `isblank` 和 `_isblank_l` 行为未定义。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istblank`|`isblank`|[\_ismbcblank](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswblank`|  
|`_istblank_l`|`_isblank_l`|[\_ismbcblank\_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswblank_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isblank`|\<ctype.h\>|  
|`iswblank`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isblank_l`|\<ctype.h\>|  
|`_iswblank_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)