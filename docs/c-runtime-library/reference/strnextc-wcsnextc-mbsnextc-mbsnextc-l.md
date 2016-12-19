---
title: "_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "_wcsnextc"
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
  - "strnextc"
  - "tcsnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "mbsnextc_l"
  - "ftcsnextc"
  - "mbsnextc"
  - "_tcsnextc"
  - "_wcsnextc"
  - "_ftcsnextc"
  - "_strnextc"
  - "wcsnextc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnextc 函数"
  - "_mbsnextc_l 函数"
  - "_strnextc 函数"
  - "_tcsnextc 函数"
  - "_wcsnextc 函数"
  - "mbsnextc 函数"
  - "mbsnextc_l 函数"
  - "strnextc 函数"
  - "tcsnextc 函数"
  - "wcsnextc 函数"
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找在字符串中的下一个字符。  
  
> [!IMPORTANT]
>  `_mbsnextc` 和 `_mbsnextc_l` 不能在 Windows 运行，执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
unsigned int _strnextc(  
   const char *str  
);  
unsigned int _wscnextc(  
   const wchar_t *str  
);   
unsigned int _mbsnextc(  
   const unsigned char *str   
);  
unsigned int _mbsnextc_l(  
   const unsigned char *str,  
   _locale_t locale  
);  
  
```  
  
#### 参数  
 `str`  
 源字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 每个这种函数返回`str`*。*中的下一个字符的整数值。  
  
## 备注  
 `_mbsnextc` 函数返回`str`中的下一个多字节字符的整数值，而不需要提升字符串指针。  `_mbsnextc` 根据当前正在使用的[多字节代码页](../../c-runtime-library/code-pages.md) 识别多字节字符序列。  
  
 如果 `str` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则将 `EINVAL` 设置为 `errno`，函数返回0。  
  
 **安全说明** 此 API 会导致由缓冲区溢出问题引起的潜在威胁。  缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnextc`|`_strnextc`|`_mbsnextc`|`_wcsnextc`|  
  
 `_strnextc` 和 `_wcsnextc` 是`_mbsnextc`的单字节字符串和宽字符字符串版本。  `_wcsnextc` 返回`string`的下一个宽字符的整数值；`_strnextc` 返回`string`的下一个单字节字符的整数值。  `_strnextc` 和 `_wcsnextc` 仅为此映射提供，不应以其他方式使用。  有关详细信息，请参阅 [使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md) 和 [一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
 `_mbsnextc_l`  相同，除非使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnextc`|\<mbstring.h\>|  
|`_mbsnextc_l`|\<mbstring.h\>|  
|`_strnextc`|\<tchar.h\>|  
|`_wcsnextc`|\<tchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strdec、\_wcsdec、\_mbsdec、\_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strinc、\_wcsinc、\_mbsinc、\_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strninc、\_wcsninc、\_mbsninc、\_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)