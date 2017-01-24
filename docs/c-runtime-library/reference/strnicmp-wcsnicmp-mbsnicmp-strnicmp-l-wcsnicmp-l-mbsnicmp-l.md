---
title: "_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l | Microsoft Docs"
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
  - "_wcsnicmp"
  - "_strnicmp_l"
  - "_wcsnicmp_l"
  - "_strnicmp"
  - "_mbsnicmp"
  - "_mbsnicmp_l"
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
  - "wcsnicmp_l"
  - "_strnicmp"
  - "_ftcsnicmp"
  - "mbsnicmp_l"
  - "_ftcsncicmp"
  - "mbsnicmp"
  - "_tcsncicmp"
  - "_mbsnicmp"
  - "_tcsnicmp"
  - "strnicmp_l"
  - "_wcsnicmp"
  - "_wcsnicmp_l"
  - "CORECRT_WSTRING/_wcsnicmp"
  - "CORECRT_WSTRING/_wcsnicmp_l"
  - "string/_strnicmp"
  - "string/_strnicmp_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsncicmp 函数"
  - "_ftcsnicmp 函数"
  - "_mbsnicmp 函数"
  - "_mbsnicmp_l 函数"
  - "_strnicmp 函数"
  - "_strnicmp_l 函数"
  - "_tcsncicmp 函数"
  - "_tcsnicmp 函数"
  - "_wcsnicmp 函数"
  - "_wcsnicmp_l 函数"
  - "字符 [C++], 比较"
  - "ftcsncicmp 函数"
  - "ftcsnicmp 函数"
  - "mbsnicmp 函数"
  - "mbsnicmp_l 函数"
  - "字符串比较 [C++], lowercase"
  - "字符串比较 [C++], strncmp 函数"
  - "字符串 [C++], 比较字符"
  - "strncmp 函数"
  - "strnicmp_l 函数"
  - "tcsncicmp 函数"
  - "tcsnicmp 函数"
  - "wcsnicmp 函数"
  - "wcsnicmp_l 函数"
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较两个字符串中指定数目的字符（不考虑大小写）。  
  
> [!IMPORTANT]
>  `_mbsnicmp` 和 `_mbsnicmp_l` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _strnicmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsnicmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsnicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strnicmp_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsnicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnicmp_l(  
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
 指示子字符串之间的关系，如下所示。  
  
|返回值|描述|  
|---------|--------|  
|\< 0|`string1` 子字符串小于 `string2` 子字符串。|  
|0|`string1` 子字符串等于 `string2` 子字符串。|  
|\> 0|`string1` 子字符串大于 `string2` 子字符串。|  
  
 参数验证错误时，这些函数返回 `_NLSCMPERROR`，该返回值是在 \<string.h\> 和 \<mbstring.h\> 中定义的。  
  
## 备注  
 `_strnicmp` 最多对 `count` 和 `string1` 的前 `string2` 字符进行序号比较。  通过将每个字符转换为小写进行不区分大小写的比较。  `_strnicmp` 是 `strncmp` 的不区分大小写版本。  如果比较 `count` 个字符之前在任一字符串中到达终止 null 字符，则比较停止。  如果比较 `count` 个字符之前在某一字符串中达到终止 null 字符时两个字符串相等，则较短的字符串较小。  
  
 ASCII 表中从 91 到 96 的字符\(“\[”、“\\”、“\]”、“^”、“\_”和“\`”\)的计算结果小于任意字母字符。  此排序等同于 `stricmp` 的排序。  
  
 `_wcsnicmp` 和 `_mbsnicmp` 分别是 `_strnicmp` 的宽字符及多字节字符版本。  `_wcsnicmp` 的参数是宽字符字符串；而 `_mbsnicmp` 的则是多字节字符字符串。  `_mbsnicmp` 根据当前的多字节代码页识别多字节字符序列，并在发生错误时返回 `_NLSCMPERROR`。  有关更多信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。  否则这三个函数否则具有相同行为。  这些函数受到区域设置的影响：没有 `_l` 后缀的版本对其与区域设置相关的行为使用当前区域设置；而带有 `_l` 后缀的版本则使用传入的 `locale`。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 所有这些函数都验证其参数。  如果 `string1` 或 `string2` 是 null 指针，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数将返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncicmp`|`_strnicmp`|`_mbsnicmp`|`_wcsnicmp`|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsncicmp_l`|`_strnicmp_l`|`_mbsnicmp_l`|`_wcsnicmp_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strnicmp`, `_strnicmp_l`|\<string.h\>|  
|`_wcsnicmp`, `_wcsnicmp_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsnicmp`, `_mbsnicmp_l`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [strncme](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) 的示例。  
  
## .NET Framework 等效项  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)