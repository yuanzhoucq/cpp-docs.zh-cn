---
title: _mbsnbset、_mbsnbset_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316580b0c5f1f46ffa9f4a49ef759b347032fc09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset、_mbsnbset_l

设置的第一个**n**的指定字符的多字节字符字符串的字节。 提供这些函数的更多安全版本；请参阅 [_mbsnbset_s、_mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md)。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*str*<br/>
要修改的字符串。

*c*<br/>
单字节或多字节字符设置。

*count*<br/>
要设置的字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsnbset**返回指向修改后的字符串的指针。

## <a name="remarks"></a>备注

**_Mbsnbset**和 **_mbsnbset_l**函数最多，设置第一个*计数*字节的*str*到*c*. 如果*计数*大于的长度*str*的长度*str*而不是使用*计数*。 如果*c*是多字节字符，不能设置完全读入指定的最后一个字节*计数*，则用空白字符填充最后一个字节。 **_mbsnbset**和 **_mbsnbset_l**不放置终止 null 末尾*str*。

**_mbsnbset**和 **_mbsnbset_l**类似于 **_mbsnset**，只不过它将设置*计数*字节而非*计数*字符的*c*。

如果*str*是**NULL**或*计数*为零，则此函数生成无效的参数异常中所述[参数验证](../../c-runtime-library/parameter-validation.md). 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**NULL**。 此外，如果*c*不是有效的多字节字符， **errno**设置为**EINVAL**改为使用空格。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 **_Mbsnbset**的此函数版本使用当前区域设置区域设置相关的行为; **_mbsnbset_l**版本是相同，但它使用改用已传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**安全说明** 此 API 会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

### <a name="output"></a>输出

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
