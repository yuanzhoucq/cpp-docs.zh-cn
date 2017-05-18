---
title: "_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
dev_langs:
- C++
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
caps.latest.revision: 28
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 3502f864ce5450e86acd673d2911ed7f5393e5fe
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l
执行不区分大小写的字符串比较。  
  
> [!IMPORTANT]
>  `_mbsicmp` 和 `_mbsicmp_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _stricmp(  
   const char *string1,  
   const char *string2   
);  
int _wcsicmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricmp_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicmp_l(  
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
 返回值指示 `string1` 和 `string2` 之间的关系，如下所示。  
  
|返回值|描述|  
|------------------|-----------------|  
|< 0|`string1` 小于 `string2`|  
|0|`string1` 等于 `string2`|  
|> 0|`string1` 大于 `string2`|  
  
 发生错误时，`_mbsicmp` 返回 `_NLSCMPERROR`，该返回值是在 \<string.h> 和 \<mbstring.h> 中定义的。  
  
## <a name="remarks"></a>备注  
 `_stricmp` 函数在将 `string1` 和 `string2` 的每个字符转换为小写之后按序号对它们进行比较，并返回一个指示它们关系的值。 `_stricmp` 与 `_stricoll` 的不同之处在于 `_stricmp` 比较仅受到会确定字符大小写的 `LC_CTYPE` 影响。 `_stricoll` 函数根据区域设置的 `LC_CTYPE` 和 `LC_COLLATE` 类别来比较字符串，其中该区域设置包括大小写和排序规则顺序。 有关 `LC_COLLATE` 类别的详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和[区域设置类别](../../c-runtime-library/locale-categories.md)。 不带 `_l` 后缀的函数的版本会将当前区域设置用于区域设置相关行为。 带后缀的版本是相同的，只不过它们转而使用传入的区域设置。 如果尚未设置区域设置，则使用 C 区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
> [!NOTE]
>  `_stricmp` 与 `_strcmpi` 相等。 它们可以互换使用，但 `_stricmp` 是首选标准。  
  
 `_strcmpi` 函数等同于 `_stricmp`，且仅提供给向后兼容。  
  
 因为 `_stricmp` 进行小写比较，所以它可能导致意外行为。  
  
 为了说明何时通过 `_stricmp` 进行大小写转换会影响比较结果，假定你有两个字符串“JOHNSTON”和“JOHN_HENRY”。 字符串 JOHN_HENRY 被视为小于 JOHNSTON，因为“_”的 ASCII 值小于小写的 S。实际上，ASCII 值介于 91 和 96 之间的任何字符都将被视为小于任何字母。  
  
 如果使用 [strcmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) 函数而不是 `_stricmp`，则“JOHN_HENRY”将大于“JOHNSTON”。  
  
 `_wcsicmp` 和 `_mbsicmp` 分别是 `_stricmp` 的宽字符及多字节字符版本。 `_wcsicmp` 的参数和返回值是宽字符字符串；而 `_mbsicmp` 的则是多字节字符字符串。 `_mbsicmp` 根据当前的多字节代码页识别多字节字符序列，并在发生错误时返回 `_NLSCMPERROR`。 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 否则这三个函数否则具有相同行为。  
  
 `_wcsicmp` 和 `wcscmp` 行为方式相同，只不过 `wcscmp` 不会在进行比较前将其参数转换为小写。 `_mbsicmp` 和 `_mbscmp` 行为方式相同，只不过 `_mbscmp` 不会在进行比较前将其参数转换为小写。  
  
 为了让 `_wcsicmp` 使用 Latin 1 字符，你将需要调用 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 默认情况下，C 区域设置有效，因此，例如，ä 比较时不会等于 Ä。 在调用 `setlocale` 前，使用 C 区域设置以外的任何区域设置调用 `_wcsicmp`。 下面的示例演示了 `_wcsicmp` 如何受区域设置影响：  
  
```  
// crt_stricmp_locale.c  
#include <string.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main() {  
   setlocale(LC_ALL,"C");   // in effect by default  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails  
   setlocale(LC_ALL,"");  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds  
}  
```  
  
 一种替代方法是调用 [_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)，并将返回的区域设置对象以参数形式传递给 `_wcsicmp_l`。  
  
 所有这些函数都验证其参数。 如果 `string1` 或 `string2` 是空指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `_NLSCMPERROR` 并将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicmp`|`_stricmp`|`_mbsicmp`|`_wcsicmp`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_stricmp`, `_stricmp_l`|\<string.h>|  
|`_wcsicmp`, `_wcsicmp_l`|\<string.h> 或 \<wchar.h>|  
|`_mbsicmp`, `_mbsicmp_l`|\<mbstring.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_stricmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
```Output  
Compare strings:  
   The quick brown dog jumps over the lazy fox  
   The QUICK brown dog jumps over the lazy fox  
  
   strcmp:   String 1 is greater than string 2  
   _stricmp:  String 1 is equal to string 2  
```  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp、_memicmp_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)
