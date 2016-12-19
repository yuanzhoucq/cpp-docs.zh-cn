---
title: "_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strncoll"
  - "_mbsncoll_l"
  - "_wcsncoll"
  - "_wcsncoll_l"
  - "_mbsncoll"
  - "_strncoll_l"
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
  - "mbsncoll_l"
  - "strncoll"
  - "_wcsncoll"
  - "_tcsnccoll"
  - "_ftcsnccoll"
  - "wcsncoll"
  - "_mbsncoll"
  - "wcsncoll_l"
  - "strncoll_l"
  - "_ftcsncoll"
  - "_strncoll"
  - "_tcsncoll"
  - "mbsncoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsnccoll 函数"
  - "_ftcsncoll 函数"
  - "_mbsncoll 函数"
  - "_mbsncoll_l 函数"
  - "_strncoll 函数"
  - "_strncoll_l 函数"
  - "_tcsnccoll 函数"
  - "_tcsncoll 函数"
  - "_wcsncoll 函数"
  - "_wcsncoll_l 函数"
  - "代码页, 用于字符串比较"
  - "ftcsnccoll 函数"
  - "ftcsncoll 函数"
  - "mbsncoll 函数"
  - "mbsncoll_l 函数"
  - "字符串 [C++], 按代码页进行比较"
  - "strncoll 函数"
  - "strncoll_l 函数"
  - "tcsnccoll 函数"
  - "tcsncoll 函数"
  - "wcsncoll 函数"
  - "wcsncoll_l 函数"
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用特定于区域设置的信息比较字符串。  
  
> [!IMPORTANT]
>  `_mbsncoll` 和 `_mbsncoll_l` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _strncoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsncoll(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strncoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsncoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsncoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `string1, string2`  
 要比较的 null 终止的字符串。  
  
 `count`  
 要比较的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 其中每个函数返回一个值，该值指示 `string1` 和 `string2` 的子字符串的关系，如下所示。  
  
|返回值|string1 与 string2 的关系|  
|---------|---------------------------|  
|\< 0|`string1` 小于 `string2`。|  
|0|`string1` 等于 `string2`。|  
|\> 0|`string1` 大于 `string2`。|  
  
 其中每个函数都会返回 `_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，请包括 STRING.h 或 MBSTRING.h。  如果 `_wcsncoll` 或 `string1` 包含排序序列域外部的宽字符代码，则 `string2` 会失败。  发生错误时，`_wcsncoll` 可能会将 `errno` 设置为 `EINVAL`。  若要检查有关调用 `_wcsncoll` 的错误，请将 `errno` 设置为 0，然后在调用 `errno` 后检查 `_wcsncoll`。  
  
## 备注  
 其中每个函数根据当前使用的代码页对 `count` 和 `string1` 中的前 `string2` 个字符进行区分大小写比较。  仅在以下情况下使用这些函数：代码页中的字符集顺序和字典字符顺序存在差异，以及此差异对于字符串比较很有用。  字符集顺序与区域设置相关。  不带 `_l` 后缀的函数版本使用当前区域设置，而带 `_l` 后缀的函数版本使用已传入的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 所有这些函数都验证其参数。  如果 `string1` 或 `string2` 为 null 指针，或 `count` 大于 `INT_MAX`，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数将返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnccoll`|`_strncoll`|`_mbsncoll`|`_wcsncoll`|  
|`_tcsncoll`|`_strncoll`|[\_mbsnbcoll](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsncoll`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strncoll`, `_strncoll_l`|\<string.h\>|  
|`_wcsncoll`, `_wcsncoll_l`|\<wchar.h\> 或 \<string.h\>|  
|`_mbsncoll`, `_mbsncoll_l`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
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