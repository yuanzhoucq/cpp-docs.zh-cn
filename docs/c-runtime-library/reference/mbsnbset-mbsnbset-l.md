---
title: "_mbsnbset、_mbsnbset_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbset
- _mbsnbset_l
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
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
dev_langs:
- C++
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: 24
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
ms.openlocfilehash: a9db88e2797e5828a007c21fd7f7fdde135ff4bf
ms.lasthandoff: 02/24/2017

---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset、_mbsnbset_l
将一个多字节字符串的前 `n` 个字节设置为指定字符。 提供这些函数的更多安全版本；请参阅 [_mbsnbset_s、_mbsnbset_s_l](../../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char *_mbsnbset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnbset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 要修改的字符串。  
  
 `c`  
 单字节或多字节字符设置。  
  
 `count`  
 要设置的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_mbsnbset` 返回指向修改后的字符串的指针。  
  
## <a name="remarks"></a>备注  
 `_mbsnbset` 和 `_mbsnbset_l` 函数最多将 `str` 的前 `count` 个字节设置为 `c`。 如果 `count` 大于 `str` 的长度，则会使用 `str` 的长度而使用 `count`。 如果 `c` 是多字节字符，且不能完全设置到由 `count` 指定的最后一个字节中，则用空白字符填充最后一个字节。 `_mbsnbset` 和 `_mbsnbset_l` 未在 `str` 的末尾放置终止 null。  
  
 `_mbsnbset` 和 `_mbsnbset_l` 与 `_mbsnset` 相似，但其设置 `count` 字节而非 `c` 的 `count` 字符。  
  
 如果 `str` 为 `NULL` 或 `count` 为零，则此函数将生成无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。 此外，如果 `c` 不是有效的多字节字符，则将 `errno` 设置为 `EINVAL`，并改用一个空格。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 此函数的 `_mbsnbset` 版本对与区域设置相关的行为使用当前区域设置，`_mbsnbset_l` 版本基本相同，但它使用传入的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 **安全说明** 此 API 会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbsnbset`|\<mbstring.h>|  
|`_mbsnbset_l`|\<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_mbsnbset.c  
// compile with: /W3  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset( string, '*', 4 ); // C4996  
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Before: This is a test  
After:  **** is a test  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)
