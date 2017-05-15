---
title: "_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 4291a8027dd01c705642af0d3651cc2fbf1277cb
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l
使用特定于区域设置的信息比较字符串。  
  
> [!IMPORTANT]
>  `_mbsicoll` 和 `_mbsicoll_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `string1, string2`  
 要比较的 null 终止的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 其中每个函数返回一个值，该值的关系`string1`到`string2`、，如下所示。  
  
|返回值|string1 与 string2 的关系|  
|------------------|----------------------------------------|  
|< 0|`string1` 小于 `string2`|  
|0|`string1` 等于 `string2`|  
|> 0|`string1` 大于 `string2`|  
|`_NLSCMPERROR`|出现了错误。|  
  
 其中每个函数都会返回 `_NLSCMPERROR`。 若要使用 `_NLSCMPERROR`，包括 `STRING.H` 或 `MBSTRING.H`。 如果 `string1` 或 `string2` 包含排序序列域外部的宽字符代码，则 `_wcsicoll` 会失败。 发生错误时，`_wcsicoll` 可能会将 `errno` 设置为 `EINVAL`。 若要检查有关调用 `_wcsicoll` 的错误，请将 `errno` 设置为 0，然后在调用 `_wcsicoll` 后检查 `errno`。  
  
## <a name="remarks"></a>备注  
 其中每个函数根据当前使用的代码页对 `string1` 和 `string2` 进行不区分大小写比较。 仅在当前代码页中的字符集顺序与字典字符顺序之间存在差异，并且此差异对于字符串比较有关系时，才应使用这些函数。  
  
 `_stricmp` 与 `_stricoll` 的不同之处在于，`_stricmp` 比较受 `LC_CTYPE` 的影响，而 `_stricoll` 的比较根据区域设置的 `LC_CTYPE` 和 `LC_COLLATE` 类别进行。 有关 `LC_COLLATE` 类别的详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [区域设置类别](../../c-runtime-library/locale-categories.md)。 这些不带 `_l` 后缀的函数的版本使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 所有这些函数都验证其参数。 如果 `string1` 或 `string2` 是 `NULL` 指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_stricoll`, `_stricoll_l`|\<string.h>|  
|`_wcsicoll`, `_wcsicoll_l`|\<wchar.h>、\<string.h>|  
|`_mbsicoll`, `_mbsicoll_l`|\<mbstring.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
