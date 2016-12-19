---
title: "_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l | Microsoft Docs"
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
  - "_strupr_s"
  - "_strupr_s_l"
  - "_mbsupr_s"
  - "_wcsupr_s_l"
  - "_mbsupr_s_l"
  - "_wcsupr_s"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strupr_s"
  - "mbsupr_s"
  - "wcsupr_s"
  - "_mbsupr_s_l"
  - "mbsupr_s_l"
  - "wcsupr_s_l"
  - "_wcsupr_s"
  - "_tcsupr_s_l"
  - "_mbsupr_s"
  - "_tcsupr_s"
  - "strupr_s_l"
  - "_wcsupr_s_l"
  - "_strupr_s"
  - "_strupr_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsupr_s 函数"
  - "_mbsupr_s_l 函数"
  - "_strupr_s 函数"
  - "_strupr_s_l 函数"
  - "_tcsupr_s 函数"
  - "_tcsupr_s_l 函数"
  - "_wcsupr_s 函数"
  - "_wcsupr_s_l 函数"
  - "转换大小写, CRT 函数"
  - "mbsupr_s 函数"
  - "mbsupr_s_l 函数"
  - "字符串转换 [C++], 大小写"
  - "字符串 [C++], 大小写"
  - "字符串 [C++], 转换大小写"
  - "strupr_s 函数"
  - "strupr_s_l 函数"
  - "tcsupr_s 函数"
  - "tcsupr_s_l 函数"
  - "大写, 将字符串转换为"
  - "wcsupr_s 函数"
  - "wcsupr_s_l 函数"
ms.assetid: 82d3a273-9f6f-4a26-9560-919d891e4581
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为大写，使用当前区域设置或通过的指定区域设置。  [\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbsupr_s` 和 `_mbsupr_s_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _strupr_s(  
   char *str,  
   size_t numberOfElements  
);  
errno_t _wcsupr_s(  
   wchar_t * str,  
   size_t numberOfElements  
);  
errno_t _strupr_s_l(  
   char * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _wcsupr_s_l(  
   wchar_t * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _mbsupr_s(  
   unsigned char *str,  
   size_t numberOfElements  
);  
errno_t _mbsupr_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _strupr_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _strupr_s_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 大写的字符串。  
  
 `numberOfElements`  
 缓冲区的大小。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；如果失败，则为非零错误代码。  
  
 这些函数验证其参数。  如果 `str` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则函数返回 `EINVAL` 并设置 `errno` 为 `EINVAL`。  如果 `numberOfElements` 比该字符串的长度短，函数仍然返回 `ERANGE` 并将 `errno` 设置为 `ERANGE`。  
  
## 备注  
 `_strupr_s` 函数转换，例如，在 `str` 的所有小写字母转换为大写。  `_wcsupr_s` 是 `_strupr_s`的宽字符版本。  `_mbsupr_s` 是 `_strupr_s`的多字节字符版本。  
  
 转换取决于 `LC_CTYPE` 类别设置区域设置。  其他字符不受影响。  有关`LC_CTYPE`的更多信息, 请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用区域设置通过。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsupr_s`|`_strupr_s`|`_mbsupr_s`|`_wcsupr_s`|  
|`_tcsupr_s_l`|`_strupr_s_l`|`_mbsupr_s_l`|`_wcsupr_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strupr_s`, `_strupr_s_l`|\<string.h\>|  
|`_wcsupr_s`, `_wcsupr_s_l`, `_mbsupr_s`, `_mbsupr_s_l`|\<string.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)中的示例。  
  
## .NET Framework 等效项  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)