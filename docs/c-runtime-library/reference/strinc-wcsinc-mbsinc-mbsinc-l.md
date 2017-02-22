---
title: "_strinc、_wcsinc、_mbsinc、_mbsinc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsinc"
  - "_wcsinc"
  - "_mbsinc_l"
  - "_strinc"
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
  - "mbsinc_l"
  - "_strinc"
  - "strinc"
  - "_mbsinc"
  - "_wcsinc"
  - "wcsinc"
  - "mbsinc"
  - "_mbsinc_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsinc 函数"
  - "_mbsinc_l 函数"
  - "_strinc 函数"
  - "_tcsinc 函数"
  - "_wcsinc 函数"
  - "mbsinc 函数"
  - "mbsinc_l 函数"
  - "strinc 函数"
  - "tcsinc 函数"
  - "wcsinc 函数"
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _strinc、_wcsinc、_mbsinc、_mbsinc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比字符串指针提前一个字符。  
  
> [!IMPORTANT]
>  `_mbsinc` 和 `_mbsinc_l` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/zh-cn/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
char *_strinc(    const char *current,    _locale_t locale ); wchar_t *_wcsinc(    const wchar_t *current,    _locale_t locale ); unsigned char *_mbsinc(    const unsigned char *current  ); unsigned char *_mbsinc_l(    const unsigned char *current,    _locale_t locale );   
```  
  
#### 参数  
 `current`  
 字符指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 其中每个例程都将返回一个指向紧跟 `current` 的字符的指针。  
  
## 备注  
 `_mbsinc` 函数将返回一个指向紧跟 `current` 的多字节字符的第一个字节的指针。  `_mbsinc` 根据当前正在使用的[多字节代码页](../../c-runtime-library/code-pages.md)来识别多字节字符序列；除了它改为使用传入的区域设置参数之外，`_mbsinc_l` 完全相同。  有关详细信息，请参见[区域设置](../../c-runtime-library/locale.md)。  
  
 如果已定义 `_MBCS`，则在 Tchar.h 中定义的一般文本函数 `_tcsinc` 将映射到 `_mbsinc`；如果已定义 `_UNICODE`，则将映射到 `_wcsinc`。  否则，`_tcsinc` 将映射到 `_strinc`。  `_strinc` 和 `_wcsinc` 是 `_mbsinc` 的单字节字符和宽字符版本。  仅为此映射提供 `_strinc` 和 `_wcsinc`，否则不应该使用它们。  有关更多信息，请参见[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
 如果 `current` 为 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则此函数将返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。  缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsinc`|\<mbstring.h\>|  
|`_mbsinc_l`|\<mbstring.h\>|  
|`_strinc`|\<tchar.h\>|  
|`_wcsinc`|\<tchar.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strdec、\_wcsdec、\_mbsdec、\_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strnextc、\_wcsnextc、\_mbsnextc、\_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [\_strninc、\_wcsninc、\_mbsninc、\_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)