---
title: "_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strnextc
- _mbsnextc_l
- _mbsnextc
- _wcsnextc
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
apitype: DLLExport
f1_keywords:
- strnextc
- tcsnextc
- _mbsnextc_l
- _mbsnextc
- mbsnextc_l
- ftcsnextc
- mbsnextc
- _tcsnextc
- _wcsnextc
- _ftcsnextc
- _strnextc
- wcsnextc
dev_langs:
- C++
helpviewer_keywords:
- _mbsnextc function
- _tcsnextc function
- _wcsnextc function
- tcsnextc function
- strnextc function
- mbsnextc function
- _strnextc function
- _mbsnextc_l function
- mbsnextc_l function
- wcsnextc function
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
caps.latest.revision: 20
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
ms.openlocfilehash: 2a1c5b467ba9f96af0bc8e402715a0a427c73eeb
ms.lasthandoff: 02/24/2017

---
# <a name="strnextc-wcsnextc-mbsnextc-mbsnextcl"></a>_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l
查找字符串中的下一个字符。  
  
> [!IMPORTANT]
>  `_mbsnextc` 和 `_mbsnextc_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _strnextc(  
   const char *str  
);  
unsigned int _wscnextc(  
   const wchar_t *str  
);   
unsigned int _mbsnextc(  
   const unsigned char *str   
);  
unsigned int _mbsnextc_l(  
   const unsigned char *str,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 源字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 其中每个函数均返回 `str`* 中下一个字符的整数值。*  
  
## <a name="remarks"></a>备注  
 `_mbsnextc` 函数返回 `str` 中下一个多字节字符的整数值，而不前移字符串指针。 `_mbsnextc` 根据当前使用的[多字节代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列。  
  
 如果 `str` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 `errno` 设置为 `EINVAL`，并且该函数将返回 0。  
  
 **安全说明** 此 API 会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnextc`|`_strnextc`|`_mbsnextc`|`_wcsnextc`|  
  
 `_strnextc` 和 `_wcsnextc` 是 `_mbsnextc` 的单字节字符字符串和宽字符字符串版本。 `_wcsnextc` 返回 `string` 中下一个宽字符的整数值；`_strnextc` 返回 `string` 中下一个单字节字符的整数值。 仅为此映射提供 `_strnextc` 和 `_wcsnextc`，否则不应该使用它们。 有关详细信息，请参阅[使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md)和[一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
 `_mbsnextc_l` 是相同的，只不过它改用传递的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbsnextc`|\<mbstring.h>|  
|`_mbsnextc_l`|\<mbstring.h>|  
|`_strnextc`|\<tchar.h>|  
|`_wcsnextc`|\<tchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_strdec、_wcsdec、_mbsdec、_mbsdec_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [_strinc、_wcsinc、_mbsinc、_mbsinc_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [_strninc、_wcsninc、_mbsninc、_mbsninc_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)
