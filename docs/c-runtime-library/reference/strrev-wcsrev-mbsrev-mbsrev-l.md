---
title: "_strrev、_wcsrev、_mbsrev、_mbsrev_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
dev_langs: C++
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b40acaa02a4907f0bcc49741312b55ea41224601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev、_wcsrev、_mbsrev、_mbsrev_l
反转字符串的字符。  
  
> [!IMPORTANT]
>  `_mbsrev` 和 `_mbsrev_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
char *_strrev(  
   char *str   
);  
wchar_t *_wcsrev(  
   wchar_t *str   
);  
unsigned char *_mbsrev(  
   unsigned char *str   
);  
unsigned char *_mbsrev_l(  
   unsigned char *str,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 要反转的 null 终止的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回指向修改后的字符串的指针。 没有保留任何返回值以指示错误。  
  
## <a name="remarks"></a>备注  
 `_strrev` 函数反转 `string` 中字符的顺序。 终止 null 字符保留在原位。 `_wcsrev` 和 `_mbsrev` 分别是 `_strrev` 的宽字符及多字节字符版本。 `_wcsrev` 的参数和返回值是宽字符字符串；而 `_mbsrev` 的则是多字节字符字符串。 对于 `_mbsrev`，`string` 中每个多字节字符中的字节顺序不会更改。 否则这三个函数否则具有相同行为。  
  
 `_mbsrev` 会验证其参数。 如果 `string1` 或 `string2` 是 null 指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `_mbsrev` 返回 `NULL`，并将 `errno` 设置为 `EINVAL`。 `_strrev` 和 `_wcsrev` 不会验证其参数。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些函数的版本都相同，只是不带 `_l` 后缀的函数使用当前区域设置，而带有 `_l` 后缀的函数则使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。 缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsrev`|`_strrev`|`_mbsrev`|`_wcsrev`|  
|**不适用**|**不适用**|`_mbsrev_l`|**不适用**|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_strrev`|\<string.h>|  
|`_wcsrev`|\<string.h> 或 \<wchar.h>|  
|`_mbsrev`, `_mbsrev_l`|\<mbstring.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_strrev.c  
// This program checks a string to see  
// whether it is a palindrome: that is, whether  
// it reads the same forward and backward.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* string = "Able was I ere I saw Elba";  
   int result;  
  
   // Reverse string and compare (ignore case):  
   result = _stricmp( string, _strrev( _strdup( string ) ) );  
   if( result == 0 )  
      printf( "The string \"%s\" is a palindrome\n", string );  
   else  
      printf( "The string \"%s\" is not a palindrome\n", string );  
}  
```  
  
```Output  
The string "Able was I ere I saw Elba" is a palindrome  
```  
  
## <a name="see-also"></a>请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcpy、wcscpy、_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)