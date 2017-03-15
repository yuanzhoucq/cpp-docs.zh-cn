---
title: "_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsicoll_l"
  - "_stricoll_l"
  - "_mbsicoll"
  - "_wcsicoll_l"
  - "_wcsicoll"
  - "_stricoll"
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
  - "stricoll"
  - "_stricoll"
  - "_wcsicoll"
  - "mbsicoll_l"
  - "_mbsicoll"
  - "_ftcsicoll"
  - "wcsicoll_l"
  - "_tcsicoll"
  - "mbsicoll"
  - "stricoll_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsicoll 函数"
  - "_mbsicoll 函数"
  - "_mbsicoll_l 函数"
  - "_stricoll 函数"
  - "_stricoll_l 函数"
  - "_tcsicoll 函数"
  - "_wcsicoll 函数"
  - "代码页, 用于字符串比较"
  - "ftcsicoll 函数"
  - "mbsicoll 函数"
  - "mbsicoll_l 函数"
  - "stricoll 函数"
  - "stricoll_l 函数"
  - "字符串比较 [C++], 区域性特定"
  - "字符串 [C++], 按代码页进行比较"
  - "tcsicoll 函数"
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用特定的区域设置信息，比较字符串。  
  
> [!IMPORTANT]
>  `_mbsicoll` 和 `_mbsicoll_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _stricoll(  
   const char *string1,  
   const char *string2   
);  
int _wcsicoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `string1, string2`  
 要比较的 null 终止的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数都返回一个值，该值指示 `string1` 的关系值设置为 `string2`*，* 如下所示。  
  
|返回值|string1 与 string2 的关系|  
|---------|---------------------------|  
|\< 0|`string1` 小于 `string2`|  
|0|`string1` 等于 `string2`|  
|\> 0|`string1` 大于 `string2`|  
|`_NLSCMPERROR`|发生错误。|  
  
 这些函数都返回`_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，请包括 `STRING.H` 或 `MBSTRING.H`。  如果 `string1` 或 `string2` 包含排序序列的字段之外的宽字符代码，`_wcsicoll` 会失败。  发生错误时，`_wcsicoll` 可以将 `errno` 设置为 `EINVAL`。  为检查调用`_wcsicoll`发生的错误，设置 `errno` 为0， 然后在调用 `_wcsicoll`后检查 `errno`。  
  
## 备注  
 每个函数基于当前正在使用的代码页执行 `string1` 和 `string2` 不区分大小写的比较。  只有在当前代码页中的字符集排序和字典字符存在差异时，这些函数才能使用，这些差异是字符串比较感兴趣的。  
  
 `_stricmp`与 `_stricoll`的不同之处在于 `_stricmp`比较受 `LC_CTYPE`的影响，而 `_stricoll`比较是基于区域设置的 `LC_CTYPE`和 `LC_COLLATE`类别。  有关 `LC_COLLATE`类别的更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [区域设置类别](../../c-runtime-library/locale-categories.md)。  这些不带 `_l` 后缀的函数使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用通过的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 所有这些函数都验证其参数。  如果`string1`或者`string2`是`NULL`指针，则无效的参数将会被调用，如[参数验证](../../c-runtime-library/parameter-validation.md) 中所描述。  如果允许执行继续，则这些函数返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_stricoll`, `_stricoll_l`|\<string.h\>|  
|`_wcsicoll`, `_wcsicoll_l`|\<wchar.h\>, \<string.h\>|  
|`_mbsicoll`, `_mbsicoll_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll、\_mbsnbcoll\_l、\_mbsnbicoll、\_mbsnbicoll\_l](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)