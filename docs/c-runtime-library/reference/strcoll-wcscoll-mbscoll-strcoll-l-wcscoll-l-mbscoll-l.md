---
title: "strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcscoll"
  - "_mbscoll"
  - "_mbscoll_l"
  - "strcoll"
  - "_strcoll_l"
  - "_wcscoll_l"
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
  - "wcscoll"
  - "_mbscoll"
  - "_tcscoll"
  - "_ftcscoll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "代码页, 用于字符串比较"
  - "mbscoll 函数"
  - "wcscoll_l 函数"
  - "ftcscoll 函数"
  - "wcscoll 函数"
  - "_strcoll_l 函数"
  - "tcscoll 函数"
  - "_ftcscoll 函数"
  - "_tcscoll 函数"
  - "_wcscoll_l 函数"
  - "_mbscoll 函数"
  - "strcoll_l 函数"
  - "strcoll 函数"
  - "字符串 [C++], 按代码页进行比较"
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用当前区域设置或指定的 LC\_COLLATE 转换状态类别，比较字符串。  
  
> [!IMPORTANT]
>  `_mbscoll` 和 `_mbscoll_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int strcoll(  
   const char *string1,  
   const char *string2   
);  
int wcscoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _strcoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale   
);  
int wcscoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale   
);  
int _mbscoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale   
);  
```  
  
#### 参数  
 `string1`, `string2`  
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
  
 这些函数在错误时都返回 `_NLSCMPERROR`。  若要使用 `_NLSCMPERROR`，请包括 STRING.H 或 MBSTRING.H。  如果 `string1` 或 `string2` 包含排序序列的字段之外的宽字符代码，`wcscoll` 会失败。  发生错误时，`wcscoll` 可以将 `errno` 设置为 `EINVAL`。  为检查调用`wcscoll`发生的错误，设置`errno` 为0， 然后在调用`wcscoll`后检查 `errno`。  
  
## 备注  
 每个函数基于当前正在使用的代码页执行 `string1` 和 `string2` 不区分大小写的比较。  只有在当前代码页中的字符集排序和字典字符存在差异时，这些函数才能使用，这些差异是字符串比较感兴趣的。  
  
 所有这些函数都验证其参数。  如果 `string1` 或 `string2` 是 null 指针，或者，如果 `count` 比 `INT_MAX`大，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
 两个字符串的比较是区域设置相关的操作，因为每个区域设置具有不同的字符排序规则。  这些没有`_l` 后缀的函数版本为该区域设置相关的行为使用当前线程区域设置；有 `_l` 后缀的版本与没有后缀的对应函数相同，只不过它们使用通过的区域设置作为参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscoll`|`strcoll`|`_mbscoll`|`wcscoll`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strcoll`|\<string.h\>|  
|`wcscoll`|\<wchar.h\>, \<string.h\>|  
|`_mbscoll`, `_mbscoll_l`|\<mbstring.h\>|  
|`_strcoll_l`|\<string.h\>|  
|`_wcscoll_l`|\<wchar.h\>, \<string.h\>|  
  
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