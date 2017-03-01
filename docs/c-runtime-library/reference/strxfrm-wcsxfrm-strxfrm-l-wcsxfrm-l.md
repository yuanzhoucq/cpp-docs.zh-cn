---
title: "strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs:
- C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 92144dbdc043d68d9280d2721a0aaeac3a9e3f1a
ms.lasthandoff: 02/24/2017

---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
根据区域设置特定信息转换字符串。  
  
## <a name="syntax"></a>语法  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `strDest`  
 目标字符串。  
  
 `strSource`  
 源字符串。  
  
 `count`  
 要放入到 `strDest`* 中的最大字符数。*  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回转换的字符串的长度（不算结尾的 null 字符）。 如果返回值大于或等于 `count`，则 `strDest` 的内容不可预知。 发生错误时，每个函数将设置 `errno` 并返回 `INT_MAX`。 对于无效字符，`errno` 将设置为 `EILSEQ`。  
  
## <a name="remarks"></a>备注  
 `strxfrm` 函数将由 `strSource` 指向的字符串转换为存储在 `strDest` 中新的排序格式。 进行转换并放入到结果字符串中的字符不超过 `count` 指定的字符数（含 null 字符）。 将使用区域设置的 `LC_COLLATE` 类别设置进行转换。 有关 `LC_COLLATE` 的详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 `strxfrm` 对其与区域设置相关的行为使用当前区域设置；`_strxfrm_l` 与此类似，只不过它使用传入的区域设置而不是当前区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 转换完成之后，使用两个已转换的字符串调用 `strcmp` 产生的结果与对两个原始字符串调用 `strcoll` 产生的结果相同。 与 `strcoll` 和 `stricoll` 一样，`strxfrm` 会根据需要自动处理多字节字符串。  
  
 `wcsxfrm` 是 `strxfrm` 的宽字符版本；`wcsxfrm` 的字符串参数是宽字符指针。 对于 `wcsxfrm`，在字符串转换之后，使用两个已转换的字符串调用 `wcscmp` 产生的结果与对两个原始字符串调用 `wcscoll` 产生的结果相同。 除此以外，`wcsxfrm` 和 `strxfrm` 的行为完全相同。 `wcsxfrm` 对其与区域设置相关的行为使用当前区域设置；`_wcsxfrm_l` 使用传入的区域设置而不是当前区域设置。  
  
 这些函数验证其参数。 如果 `strSource` 为空指针，或 `strDest` 为空指针（除非计数为零），或者如果 `count` 大于 `INT_MAX`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `INT_MAX`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 在“C”区域设置中，字符集（ASCII 字符集）中的字符顺序与字典中的字符顺序相同。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的字符顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“&\#x00E4;”（值 0xE4）之前，但在字典顺序中字符“ä”位于字符“a”之前。  
  
 在字符集中的字符顺序与字典中的字符顺序不同的区域设置中，请对原始字符串使用 `strxfrm`，然后对结果字符串使用 `strcmp`，以根据当前区域设置的 `LC_COLLATE` 类别设置，生成按字典顺序进行的字符串比较。 因此，若要在以上区域设置中按字典顺序比较两个字符串，请对原始字符串使用 `strxfrm`，然后对结果字符串使用 `strcmp`。 或者，可以对原始字符串使用 `strcoll` 而不是 `strcmp`。  
  
 `strxfrm` 基本上是一个带有 `LCMAP_SORTKEY` 的围绕 [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) 的包装器。  
  
 以下表达式的值是进行源字符串的 `strxfrm` 转换所需的数组的大小：  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 仅在“C”区域设置中，`strxfrm` 才等效于以下形式：  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`strxfrm`|\<string.h>|  
|`wcsxfrm`|\<string.h> 或 \<wchar.h>|  
|`_strxfrm_l`|\<string.h>|  
|`_wcsxfrm_l`|\<string.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)
