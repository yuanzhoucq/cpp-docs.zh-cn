---
title: "isdigit、iswdigit、_isdigit_l、_iswdigit_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isdigit_l"
  - "iswdigit"
  - "_iswdigit_l"
  - "isdigit"
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
  - "_iswdigit_l"
  - "_isdigit_l"
  - "iswdigit"
  - "isdigit"
  - "_istdigit"
  - "_istdigit_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iswdigit 函数"
  - "iswdigit_l 函数"
  - "_iswdigit_l 函数"
  - "_istdigit_l 函数"
  - "_istdigit 函数"
  - "istdigit 函数"
  - "isdigit 函数"
  - "isdigit_l 函数"
  - "_ismbcdigit_l 函数"
  - "_isdigit_l 函数"
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# isdigit、iswdigit、_isdigit_l、_iswdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示十进制数字字符。  
  
## 语法  
  
```  
int isdigit(   
   int c   
);  
int iswdigit(   
   wint_t c   
);  
int _isdigit_l(   
   int c,  
   _locale_t locale  
);  
int _iswdigit_l(   
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
 如果 `c` 是十进制数字字符的特定表示，则每个实例返回非零。  如果 `c` 是十进制数 \(0 – 9\),`isdigit` 返回一个非零值。  如果 `c` 是对应于十进制数字字符的宽字符,`iswdigit` 返回一个非零值。  如果 `c` 不满足测试条件，则其中每个实例返回 0。  
  
 这些带有 `_l` 后缀的函数的版本使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或在范围 0 到 0xFF 中（包含 0 和 0xFF），则 `isdigit` 和 `_isdigit_l` 行为未定义。  如果使用的是调试 CRT 库且 `c` 不是这些值之一，函数就会引发断言。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istdigit`|`isdigit`|[\_ismbcdigit](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswdigit`|  
|`_istdigit_l`|`_isdigit_l`|[\_ismbcdigit\_l](../../c-runtime-library/reference/ismbcalnum-functions.md)|`_iswdigit_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`isdigit`|\<ctype.h\>|  
|`iswdigit`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isdigit_l`|\<ctype.h\>|  
|`_iswdigit_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)