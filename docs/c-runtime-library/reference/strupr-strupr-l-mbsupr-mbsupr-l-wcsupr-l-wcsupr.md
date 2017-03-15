---
title: "_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsupr_l"
  - "_mbsupr"
  - "_strupr_l"
  - "_wcsupr"
  - "_wcsupr_l"
  - "_strupr"
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
  - "ntoskrnl.exe"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbsupr"
  - "_ftcsupr"
  - "mbsupr"
  - "_tcsupr"
  - "strupr_l"
  - "_fstrupr"
  - "_strupr"
  - "mbsupr_l"
  - "_wcsupr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstrupr 函数"
  - "_ftcsupr 函数"
  - "_mbsupr 函数"
  - "_mbsupr_l 函数"
  - "_strupr 函数"
  - "_strupr_l 函数"
  - "_tcsupr 函数"
  - "_tcsupr_l 函数"
  - "_wcsupr 函数"
  - "_wcsupr_l 函数"
  - "转换大小写, CRT 函数"
  - "fstrupr 函数"
  - "ftcsupr 函数"
  - "mbsupr 函数"
  - "mbsupr_l 函数"
  - "字符串转换 [C++], 大小写"
  - "字符串 [C++], 大小写"
  - "字符串 [C++], 转换大小写"
  - "strupr 函数"
  - "strupr_l 函数"
  - "tcsupr 函数"
  - "tcsupr_l 函数"
  - "大写, 将字符串转换为"
  - "wcsupr 函数"
  - "wcsupr_l 函数"
ms.assetid: caac8f16-c233-41b6-91ce-575ec7061b77
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为大写字母。  有关这些函数的更多安全版本，请参见 [\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsupr` 和 `_mbsupr_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strupr(  
   char *str   
);  
wchar_t *_wcsupr(  
   wchar_t *str   
);  
unsigned char *_mbsupr(  
   unsigned char *str   
);  
char *_strupr_l(  
   char *str,  
   _locale_t locale  
);  
wchar_t *_wcsupr_l(  
   wchar_t *str,  
   _locale_t locale  
);  
unsigned char *_mbsupr_l(  
   unsigned char *str,  
   _locale_t locale  
);  
template <size_t size>  
char *_strupr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strupr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 大写的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向修改后的字符串的指针。  由于修改就地完成，返回的指针与作为输入参数传递的指针相同。  没有保留任何返回值以指示错误。  
  
## 备注  
 `_strupr` 函数转换，例如，在 `str` 的所有大写字母转换为小写。  转换取决于 `LC_CTYPE` 类别设置区域设置。  其他字符不受影响。  有关`LC_CTYPE`的更多信息, 请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  这些不带 `_l` 后缀的函数使用当前区域设置；；带有 `_l` 后缀的版本相同，只不过它们使用的区域设置不同。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `_wcsupr` 和 `_mbsupr` 是宽字符，属于 `_strupr` 的多节字字符版本。  参数和 `_wcsupr` 的返回值是宽字符字符串；`_mbsupr` 的参数和返回值为多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
 如果 `str` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回原始字符串并将 `errno` 设置为 `EINVAL` 。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsupr`|`_strupr`|`_mbsupr`|`_wcsupr`|  
|`_tcsupr_l`|`_strupr_l`|`_mbsupr_l`|`_wcsupr_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strupr`, `_strupr_l`|\<string.h\>|  
|`_wcsupr`, `_wcsupr_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsupr`, `_mbsupr_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[将字符串转换成浮点数](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)示例。  
  
## .NET Framework 等效项  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)