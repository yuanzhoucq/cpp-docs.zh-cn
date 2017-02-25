---
title: "_strninc、_wcsninc、_mbsninc、_mbsninc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsninc"
  - "_mbsninc_l"
  - "_wcsninc"
  - "_strninc"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strninc"
  - "wcsninc"
  - "mbsninc_l"
  - "_strninc"
  - "_tcsninc"
  - "mbsninc"
  - "_mbsninc_l"
  - "_ftcsninc"
  - "_wcsninc"
  - "_mbsninc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsninc 函数"
  - "_mbsninc_l 函数"
  - "_strninc 函数"
  - "_tcsninc 函数"
  - "_wcsninc 函数"
  - "mbsninc 函数"
  - "mbsninc_l 函数"
  - "strninc 函数"
  - "tcsninc 函数"
  - "wcsninc 函数"
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _strninc、_wcsninc、_mbsninc、_mbsninc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过`n` 字符提升字符串指针。  
  
> [!IMPORTANT]
>  `_mbsninc` 和 `_mbsninc_l` 不能在 Windows 运行时中执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strninc(  
   const char *str,  
   size_t count   
);  
wchar_t *_wcsninc(  
   const wchar_t *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 源字符串。  
  
 `count`  
 增加字符串指针的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果所提供的指针是 `NULL`，在 `str` 由 `count` 字符或 `NULL` 增加后，每个实例返回指向 `str`的指针。  如果 `count`大于或等于`str`的字符数，返回值未定义。  
  
## 备注  
 `_mbsninc` 函数由 `count` 多字节字符增加 `str`。  `_mbsninc` 根据当前正在使用的[多字节代码页](../../c-runtime-library/code-pages.md) 识别多字节字符序列。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsninc`|`_strninc`|`_mbsninc`|`_wcsninc`|  
  
 `_strninc` 和 `_wcsninc` 是`_mbsninc`的单字节字符串和宽字符字符串版本。  `_wcsninc` 和 `_strninc` 仅为此映射提供，不应以其他方式使用。  有关详细信息，请参阅 [使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md) 和 [一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
 `_mbsninc_l` 相同，只不过它使用区域设置参数通过。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsninc`|\<mbstring.h\>|  
|`_mbsninc_l`|\<mbstring.h\>|  
|`_strninc`|\<tchar.h\>|  
|`_wcsninc`|\<tchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strdec、\_wcsdec、\_mbsdec、\_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strinc、\_wcsinc、\_mbsinc、\_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strnextc、\_wcsnextc、\_mbsnextc、\_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)