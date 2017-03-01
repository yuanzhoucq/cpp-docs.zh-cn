---
title: "_mbsnbcmp、_mbsnbcmp_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcmp
- _mbsnbcmp_l
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
- mbsnbcmp
- tcsnbmp
- _mbsnbcmp_l
- mbsnbcmp_l
- _mbsnbcmp
dev_langs:
- C++
helpviewer_keywords:
- mbsnbcmp_l function
- mbsnbcmp function
- tcsncmp function
- _mbsnbcmp_l function
- _tcsncmp function
- _mbsnbcmp function
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
caps.latest.revision: 23
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
ms.openlocfilehash: 052aed3d0897821ae617677913ed37e773f6d02d
ms.lasthandoff: 02/24/2017

---
# <a name="mbsnbcmp-mbsnbcmpl"></a>_mbsnbcmp、_mbsnbcmp_l
比较两个多字节字符字符串的前 `n` 个字节。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `string1, string2`  
 要比较的字符串。  
  
 `count`  
 要比较的字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回值指示 `string1` 和 `string` 的子字符串之间的序号关系。  
  
|返回值|描述|  
|------------------|-----------------|  
|< 0|`string1` 子字符串小于 `string2` 子字符串。|  
|0|`string1` 子字符串等于 `string2` 子字符串。|  
|> 0|`string1` 子字符串大于 `string2` 子字符串。|  
  
 参数验证错误时，`_mbsnbcmp` 和 `_mbsnbcmp_l` 返回 `_NLSCMPERROR`，该返回值是在 \<string.h> 和 \<mbstring.h> 中定义的。  
  
## <a name="remarks"></a>备注  
 `_mbsnbcmp` 函数最多比较 `count` 和 `string1` 的前 `string2` 个字节，并返回一个指示子字符串之间关系的值。 `_mbsnbcmp` 是 `_mbsnbicmp` 的区分大小写版本。 不同于 `_mbsnbcoll`，`_mbsnbcmp` 不受区域设置的排序规则顺序影响。 `_mbsnbcmp` 根据当前的多字节[代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列。  
  
 `_mbsnbcmp` 类似于 `_mbsncmp`，只不过 `_mbsncmp` 按字符（而不是按字节）对字符串进行比较。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响，它指定多字节字符的前导字节和尾随字节。 有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 `_mbsnbcmp` 函数对与区域设置相关的行为使用当前区域设置。 `_mbsnbcmp_l` 函数完全相同，只不过它转而使用 `locale` 参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `string1` 或 `string2` 是空指针，则这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则这些函数返回 `_NLSCMPERROR`，并且 `errno` 设置为 `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|---------------------------------------|--------------------|-----------------------|  
|`_tcsncmp`|[strncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|`_mbsnbcmp`|[wcsncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|  
|`_tcsncmp_l`|[strncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|`_mbsnbcml`|[wcsncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbsnbcmp`|\<mbstring.h>|  
|`_mbsnbcmp_l`|\<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_mbsnbcmp.c  
#include <mbstring.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n          %s\n", string1 );  
   printf( "          %s\n\n", string2 );  
   printf( "Function: _mbsnbcmp (first 10 characters only)\n" );  
   result = _mbsncmp( string1, string2 , 10 );  
   if( result > 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:   String 1 is %s string 2\n\n", tmp );  
   printf( "Function: _mbsnicmp _mbsnicmp (first 10 characters only)\n" );  
   result = _mbsnicmp( string1, string2, 10 );  
   if( result > 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:   String 1 is %s string 2\n\n", tmp );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Compare strings:  
          The quick brown dog jumps over the lazy fox  
          The QUICK brown fox jumps over the lazy dog  
  
Function: _mbsnbcmp (first 10 characters only)  
Result:   String 1 is greater than string 2  
  
Function: _mbsnicmp _mbsnicmp (first 10 characters only)  
Result:   String 1 is equal to string 2  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbicmp、_mbsnbicmp_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)
