---
title: "_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strtoi64"
  - "_strtoi64_l"
  - "_wcstoi64_l"
  - "_wcstoi64"
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
  - "_strtoi64"
  - "strtoi64"
  - "_stroi64_l"
  - "_wcstoi64_l"
  - "wcstoi64_l"
  - "_wcstoi64"
  - "wcstoi64"
  - "strtoi64_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtoi64 函数"
  - "_strtoi64_l 函数"
  - "_wcstoi64 函数"
  - "_wcstoi64_l 函数"
  - "字符串转换, 为整数"
  - "strtoi64 函数"
  - "strtoi64_l 函数"
  - "wcstoi64 函数"
  - "wcstoi64_l 函数"
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为 `__int64` 值。  
  
## 语法  
  
```  
__int64 _strtoi64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
__int64 _wcstoi64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
__int64 _strtoi64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
__int64 _wcstoi64_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `nptr`  
 要转换的 null 终止的字符串。  
  
 `endptr`  
 指向停止扫描字符的指针。  
  
 `base`  
 待使用的数基。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 除非表示形式导致溢出，这时返回`_I64_MAX`或`_I64_MIN`，否则 `_strtoi64` 返回该字符串`nptr`中表示的值。  如果不能执行转换，则该函数会返回 0。  `_wcstoi64` 返回值类似于 `strtoi64`。  
  
 `_I64_MAX` 和 `_I64_MIN` 在 LIMITS.H. 中进行定义。  
  
 如果 `nptr` 为 `NULL` 或者 `base` 非零和小于 2 或大于 36，则将 `errno` 设置为 `EINVAL`。  
  
 有关这些内容以及其他返回代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_strtoi64` 函数将`nptr`转换为 `__int64`。  当他们不能识别的第一个数字字符出现时，函数都停止读入字符串 `nptr`。  这可能是终止空字符，也可能是大于或等于 `base` 的第一个数字字符。  `_wcstoi64` 是 `_strtoi64` 的宽字符版本；其 `nptr` 参数是宽字符字符串。  否则这些函数具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstoi64`|`_strtoi64`|`_strtoi64`|`_wcstoi64`|  
|`_tcstoi64_l`|`_strtoi64_l`|`_strtoi64_l`|`_wcstoi64_l`|  
  
 区域设置的`LC_NUMERIC` 类别设置确定 `nptr`*;*中基数字符的识别；有关详细信息，请参阅[设置区域设置](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  无\_l后缀的函数使用当前区域设置; `_strtoi64_l`和`_wcstoi64_l`与无 `_l` 后缀的相应函数是相同的，不同之处在于它们改用传递的区域设置.  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，停止扫描的字符指针将存储在 `endptr` 指向的位置。  如果没有转换（未找到有效数字或指定了无效基础），`nptr` 的值存储在 `endptr` 指向的位置。  
  
 `_strtoi64` 希望`nptr`指向以下格式的字符串：  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits`\]  
  
 被忽略的是`whitespace` 可能包含空格和制表符；`digits` 是一个或多个十进制数字。  不符合此窗体的首个字符将终止扫描。  如果 `base` 在 2 和 36 之间，则将它用作数字的基础。  如果 `base` 是 0，则通过使用 `nptr` 所指向的初始字符串字符确定基项。  如果首个字符为0，而第二个字符不为“X”或“Y”，该字符串则被翻译成八进制整数。  如果首个字符为“0”，而第二个字符为“X”或“Y”，该字符串则被解读为十六进制整数。  如果第一个字符为“1”到“9”，该字符串被解读为十进制整数。  字母“a”到“z”（或“A”到“Z”）赋值 10 到 35；只允许使用赋值小于 `base` 的字母。  在基项范围外的第一个字符将终止扫描。  例如，如果 `base` 为 0 且扫描的第一个字符也为“0”，则会假定为一个八进制整数且字符“8”或“9”将会终止扫描。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strtoi64`, `_strtoi64_l`|\<stdlib.h\>|  
|`_wcstoi64`, `_wcstoi64_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)