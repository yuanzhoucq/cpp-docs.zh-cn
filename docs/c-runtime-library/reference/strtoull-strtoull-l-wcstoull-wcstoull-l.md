---
title: "strtoull、_strtoull_l、wcstoull、_wcstoull_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strtoull_l"
  - "_wcstoull_l"
  - "strtoull"
  - "wcstoull"
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
  - "_wcstoull_l"
  - "_tcstoull"
  - "_tcstoull_l"
  - "wcstoull"
  - "_strtoull_l"
  - "strtoull"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtoull_l 函数"
  - "_tcstoull 函数"
  - "_tcstoull_l 函数"
  - "_wcstoull_l 函数"
  - "strtoull 函数"
  - "wcstoull 函数"
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# strtoull、_strtoull_l、wcstoull、_wcstoull_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为无符号长整数值。  
  
## 语法  
  
```  
unsigned long long strtoull(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long long _strtoull_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long long wcstoull(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long long _wcstoull_l(  
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
 指向停止扫描的字符的指针。  
  
 `base`  
 待使用的数基。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果任何或 `ULLONG_MAX` 在溢出时，则 `strtoull` 返回转换后的值。  如果不能执行转换，则 `strtoull` 返回 0。  `wcstoull` 返回值类似于 `strtoull`。  对于两个函数，如果出现溢出或下溢，请将 `errno` 设置为 `ERANGE`。  
  
 有关返回代码的详细信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个函数将输入字符串 `nptr` 转换为 `unsigned long long` 整数值。  
  
 `strtoull` 在发现第一个不能将其识别为数字的字符时，将停止读入字符串 `nptr`。  这可能是终止 null 字符，也可能是大于或等于 `base` 的第一个数字字符。  区域设置的 `LC_NUMERIC` 类别设置确定 `nptr` 中基数字符的识别；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  `strtoull` 和 `wcstoull` 使用当前区域设置；`_strtoull_l` 和 `_wcstoull_l` 改用传递区域设置，但仍相同。  有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，停止扫描的字符指针将存储在 `endptr` 指向的位置。  如果不能指向转换（未找到有效数字或指定了无效基础），`nptr` 的值存储在 `endptr` 指向的位置。  
  
 `wcstoull` 是 `strtoull` 的宽字符版本；而且其 `nptr` 参数是宽字符字符串。  否则这三个函数否则具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstoull`|`strtoull`|`strtoull`|`wcstoull`|  
|`_tcstoull_l`|`strtoull_l`|`_strtoull_l`|`_wcstoull_l`|  
  
 `strtoull` 希望 `nptr` 指向以下格式的字符串：  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits` &#124; \[`letters`\]\]  
  
 `whitespace` 可能包含已忽略的空格和制表符；`digits` 是一个或多个十进制数字；`letters` 是从“a”到“z”（或“A”到“Z”）的一个或多个字母。  不符合此窗体的首个字符将终止扫描。  如果 `base` 在 2 和 36 之间，则将它用作数字的基础。  如果 `base` 是 0，则通过使用 `nptr` 所指向的初始字符串字符确定基项。  如果首个字符为“0”，而第二个字符不为“X”或“Y”，该字符串则被解读为八进制整数。  如果首个字符为“0”，而第二个字符为“X”或“Y”，该字符串则被解读为十六进制整数。  如果第一个字符为“1”到“9”，该字符串被解读为十进制整数。  字母“a”到“z”（或“A”到“Z”）赋值 10 到 35；只允许使用赋值小于 `base` 的字母。  在基项范围外的第一个字符将终止扫描。  例如，如果 `base` 为 0 且扫描的第一个字符也为“0”，则会假定一个八进制整数且字符“8”或“9”会终止扫描。  `strtoull` 允许加号 \(`+`\) 或减号 \(`–`\) 前缀；前导减号表示返回值为负。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strtoull`|\<stdlib.h\>|  
|`wcstoull`|\<stdlib.h\> 或 \<wchar.h\>|  
|`_strtoull_l`|\<stdlib.h\>|  
|`_wcstoull_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[将字符串转换成浮点数](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)示例。  
  
## .NET Framework 等效项  
 [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll、\_strtoll\_l、wcstoll、\_wcstoll\_l](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)