---
title: strcmp、wcscmp、_mbscmp | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs:
- C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df2168da257c6d1d07cff6400122830da60b5fef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp、wcscmp、_mbscmp

比较字符串。

> [!IMPORTANT]
> **_mbscmp**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
```

### <a name="parameters"></a>参数

*string1*， *string2*<br/>
要比较的 null 终止的字符串。

## <a name="return-value"></a>返回值

其中每个函数的返回值指示的序号关系*string1*到*string2*。

|值|string1 与 string2 的关系|
|-----------|----------------------------------------|
|< 0|*string1*是小于*string2*|
|0|*string1*等同于*string2*|
|> 0|*string1*大于*string2*|

参数验证错误时， **_mbscmp**返回 **_NLSCMPERROR**中, 定义\<string.h > 和\<mbstring.h >。

## <a name="remarks"></a>备注

**Strcmp**函数执行的序号比较*string1*和*string2*并返回一个值，指示二者关系。 **wcscmp**和 **_mbscmp**分别是宽字符及多字节字符版本的**strcmp**。 **_mbscmp**根据当前的多字节代码页识别多字节字符序列，并返回 **_NLSCMPERROR**发生错误时。 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 此外，如果*string1*或*string2*是 null 指针， **_mbscmp**中所述调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md). 如果允许执行继续，则 **_mbscmp**返回 **_NLSCMPERROR**和设置**errno**到**EINVAL**。 **strcmp**和**wcscmp**不会验证其参数。 否则这三个函数否则具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp**函数与不同**strcoll**在于**strcmp**比较序号，并且不受区域设置。 **strcoll**使用按字典顺序比较字符串**LC_COLLATE**的当前区域设置的类别。 有关详细信息**LC_COLLATE**类别，请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)。

在“C”区域设置中，字符集 (ASCII 字符集) 中的字符顺序与字典中的字符顺序一样。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“ä”（值 0xE4）之前，但在字典顺序中，字符“ä”位于字符“a”之前。

在为其字符集和字典字符顺序不同的区域设置中，你可以使用**strcoll**而不是**strcmp**字典对字符串进行比较。 或者，可以使用**strxfrm**对原始字符串，以及然后使用**strcmp**对结果字符串。

**Strcmp**函数是区分大小写。 **_stricmp**， **_wcsicmp**，和 **_mbsicmp**比较的第一个将它们转换为小写形式的字符串。 两个包含位于 Z 之间的字符的字符串和 'a' ASCII 表中 (['，'\\，]，^，'_' 和 '\`) 比较不同，具体取决于其大小写。 例如，两个字符串"ABCDE"和"ABCD ^"比较的一种方法，如果比较采用小写形式 ("abcde">"abcd ^") 和另一种方法 ("ABCDE"<"ABCD ^") 如果比较采用大写形式。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strcmp**|<string.h>|
|**wcscmp**|<string.h> 或 <wchar.h>|
|**_mbscmp**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_strcmp.c

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
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
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

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp、_memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
