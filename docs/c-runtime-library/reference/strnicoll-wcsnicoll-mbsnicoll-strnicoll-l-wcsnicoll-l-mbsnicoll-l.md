---
title: "_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnicoll_l"
  - "_mbsnicoll"
  - "_wcsnicoll_l"
  - "_strnicoll"
  - "_strnicoll_l"
  - "_wcsnicoll"
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
  - "wcshicoll_l"
  - "_ftcsncicoll"
  - "strnicoll_l"
  - "_wcsnicoll"
  - "mbsnicoll_l"
  - "_strnicoll"
  - "mbsnicoll"
  - "_ftcsnicoll"
  - "wcsnicoll"
  - "_tcsnicoll"
  - "_mbsnicoll"
  - "strinicoll"
  - "_tcsncicoll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsncicoll 函数"
  - "_ftcsnicoll 函数"
  - "_mbsnicoll 函数"
  - "_mbsnicoll_l 函数"
  - "_strnicoll 函数"
  - "_strnicoll_l 函数"
  - "_tcsncicoll 函数"
  - "_tcsnicoll 函数"
  - "_wcsnicoll 函数"
  - "_wcsnicoll_l 函数"
  - "代码页, 用于字符串比较"
  - "ftcsncicoll 函数"
  - "ftcsnicoll 函数"
  - "mbsnicoll 函数"
  - "mbsnicoll_l 函数"
  - "字符串 [C++], 按代码页进行比较"
  - "strnicoll 函数"
  - "strnicoll_l 函数"
  - "tcsncicoll 函数"
  - "tcsnicoll 函数"
  - "wcsnicoll 函数"
  - "wcsnicoll_l 函数"
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用特定的区域设置信息比较字符串。  
  
> [!IMPORTANT]
>  `_mbsnicoll` 和 `_mbsnicoll_l` 不能在 Windows 运行时的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _strnicoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsnicoll(  
   const wchar_t *string1,  
   const wchar_t *string2 ,  
   size_t count   
);  
int _mbsnicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strnicoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsnicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2 ,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `string1, string2`  
 要比较的以 null 终止的字符串。  
  
 `count`  
 要比较的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数都返回一个指示 `string1` 和 `string2`子字符串关系的值*，* 如下所示。  
  
|返回值|string1 与 string2 的关系|  
|---------|---------------------------|  
|\< 0|`string1` 小于 `string2`|  
|0|`string1` 等于 `string2`|  
|\> 0|`string1` 大于 `string2`|  
  
 这些函数都返回`_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，请包括 STRING.H 或 MBSTRING.H。  如果 `string1` 或 `string2` 包含排序序列的字段之外的宽字符代码，`_wcsnicoll` 会失败。  发生错误时，`_wcsnicoll` 可以将 `errno` 设置为 `EINVAL`。  为检查调用`_wcsnicoll`发生的错误，设置 `errno` 为0， 然后在调用 `_wcsnicoll`**.**后，检查 `errno`。  
  
## 备注  
 每一个这些函数在 `string1` 和 `string2`中，根据代码页执行首个 `count` 字符的不区分大小写的比较。  只有当对字符集排序时和代码页中字典字符的排序不同，并且字符串比较时产生不同利益时，才应使用这些功能。  不包含 `_l` 后缀的这些函数的版本使用当前的区域设置和代码页。  包含`_l`后缀的版本是相同的，只不过它们使用的传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 所有这些函数都验证其参数。  如果 `string1` 或 `string2` 是 null 指针，或者，如果计数大于 `INT_MAX`，z\=则会调用无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`**.**  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncicoll`|`_strnicoll`|`_mbsnbicoll`|`_wcsnicoll`|  
|`_tcsnicoll`|`_strnicoll`|[\_mbsnbicoll](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsnicoll`|  
|`_tcsnicoll_l`|`_strnicoll_l`|`_mbsnbicoll_l`|`_wcsnicoll_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strnicoll`, `_strnicoll_l`|\<string.h\>|  
|`_wcsnicoll`, `_wcsnicoll_l`|\<wchar.h\> 或 \<string.h\>|  
|`_mbsnicoll`, `_mbsnicoll_l`|\<mbstring.h\>|  
  
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