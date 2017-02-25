---
title: "_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbicoll_l"
  - "_mbsnbcoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
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
  - "mbsnbicoll"
  - "mbsnbcoll"
  - "mbsnbicoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
  - "_ftcsnicoll"
  - "_ftcsncoll"
  - "mbsnbcoll_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcoll 函数"
  - "_mbsnbcoll_l 函数"
  - "_mbsnbicoll 函数"
  - "_mbsnbicoll_l 函数"
  - "_tcsncoll 函数"
  - "_tcsnicoll 函数"
  - "mbsnbcoll 函数"
  - "mbsnbcoll_l 函数"
  - "mbsnbicoll 函数"
  - "mbsnbicoll_l 函数"
  - "tcsncoll 函数"
  - "tcsnicoll 函数"
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用多字节代码页信息，比较两个多字节字符字符串的`n` 字节。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _mbsnbcoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnbicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `string1, string2`  
 用于比较的字符串。  
  
 `count`  
 比较的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回暗示`string1` 和 `string2`子字符串关系的值。  
  
|返回值|描述|  
|---------|--------|  
|\< 0|`string1` 子字符串小于 `string2` 子字符串。|  
|0|`string1` 子字符串与 `string2` 子字符串相同。|  
|\> 0|`string1` 子字符串大于 `string2` 子字符串|  
  
 如果 `string1` 或 `string2` 是`NULL`，或者，`count`比`INT_MAX`大，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些函数返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  若要使用 `_NLSCMPERROR`，请包括 String.h 或 Mbstring.h。  
  
## 备注  
 这些函数至多检查 `string1` 和 `string2` 的第一个 `count`字节，并返回暗示`string1` 和 `string2` 子字符串之间的关系的值。  如果 `string1` 或 `string2` 子字符串的最终字节是前导字节，不包括在该比较中；这些函数仅比较在子字符串的完整字符。  `_mbsnbicoll` 是 `_mbsnbcoll` 的一个不区分大小写的版本。  就像`_mbsnbcmp` 和 `_mbsnbicmp`，`_mbsnbcoll` 和 `_mbsnbicoll` 校对基于当前正在使用的多字节 [代码页](../../c-runtime-library/code-pages.md)指定的字典序列的两个多字节字符字符串。  
  
 对于某些代码页和对应的字符集，该字符集的字符序列可能与字典字符排序不同。  在“C”区域设置，这不是用例：ASCII 字符集中的字符排序与字符的字典排序相同。  但是，在某些欧洲代码页中，例如，在字符集中，字符“a”\(值 0x61\) 位于字符“ä”\(值 0xE4\)之前，但是，在字典序列中，字符“ä”在字符" a ”之前。  在一个实例中，若要按字节对字符串进行字典序列的比较，请使用 `_mbsnbcoll` 而不是 `_mbsnbcmp`;仅检查字符串是相等的，请使用 `_mbsnbcmp`。  
  
 由于 `coll`函数按字典顺序校对字符串的比较，而 `cmp` 函数简单地测试字符串的相等，`coll` 函数执行起来比`cmp`的相关版本慢。  因此，`coll`函数只能使用在字符集顺序和当前代码页的字典字符顺序存在区别时，且该区别引起了比较的不同。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncoll`|[\_strncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll`|[\_wcsncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsncoll_l`|[\_strncoll、\_wcsncoll、\_mbsncoll、\_strncoll\_l、\_wcsncoll\_l、\_mbsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll_l`|[\_wcsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsnicoll`|[\_strnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll`|[\_wcsnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
|`_tcsnicoll_l`|[\_strnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll_l`|[\_wcsnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsnbcoll`|\<mbstring.h\>|  
|`_mbsnbcoll_l`|\<mbstring.h\>|  
|`_mbsnbicoll`|\<mbstring.h\>|  
|`_mbsnbicoll_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp、\_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)