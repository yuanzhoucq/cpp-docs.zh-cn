---
title: "_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
dev_langs: C++
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb2434cf25e6746637c13cdf8df7725555e839c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
返回指定计数内的字符数或字节数。  
  
> [!IMPORTANT]
>  `_mbsnbcnt`、`_mbsnbcnt_l`、`_mbsnccnt` 和 `_mbsnccnt_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 要检查的字符串。  
  
 `count`  
 要在 `str` 中检查的字符数或字节数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 返回在 `str` 的前 `count` 个多字节字符中找到的字节数。 `_mbsnccnt` 和 `_mbsnccnt_l` 返回在 `str` 的前 `count` 个字节中找到的字符数。 如果在完成 `str` 的检查之前遇到 NULL 字符，则它们返回在此 NULL 字符之前找到的字节数或字符数。 如果 `str` 包含的字符或字节少于 `count` 个，则它们返回字符串中的字符数或字节数。 如果 `count` 小于零，则它们返回 0。 在以前的版本中，这些函数的返回值类型为 `int`，而不是 `size_t`。  
  
 `_strncnt` 返回单字节字符串 `str` 的前 `count` 个字节中的字符数。 `_wcsncnt` 返回宽字符字符串 `str` 的前 `count` 个宽字符中的字符数。  
  
## <a name="remarks"></a>备注  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 计数在 `str` 的前 `count` 个多字节字符中找到的字节数。 `_mbsnbcnt` 和 `_mbsnbcnt_l` 替换 `mtob`，而且应该用于代替 `mtob`。  
  
 `_mbsnccnt` 和 `_mbsnccnt_l` 计数在 `str` 的前 `count` 个字节中找到的字符数。 如果 `_mbsnccnt` 和 `_mbsnccnt_l` 在双字节字符的第二个字节中遇到一个 NULL，则第一个字节也被视为 NULL，并且不包括在返回的计数值中。 `_mbsnccnt` 和 `_mbsnccnt_l` 替换 `btom`，而且应该用于代替 `btom`。  
  
 如果 `str` 是空指针，或者 `count` 是 0，则这些函数调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，`errno` 设置为 `EINVAL`，且函数返回 0。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|-------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbsnbcnt`|\<mbstring.h>|  
|`_mbsnbcnt_l`|\<mbstring.h>|  
|`_mbsnccnt`|\<mbstring.h>|  
|`_mbsnccnt_l`|\<mbstring.h>|  
|`_strncnt`|\<tchar.h>|  
|`_wcsncnt`|\<tchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## <a name="output"></a>输出  
  
```  
The first 10 characters are single-byte.  
```  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)