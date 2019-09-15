---
title: strcmp、wcscmp、_mbscmp、_mbscmp_l
ms.date: 01/22/2019
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 4bef0c61122e93bd45bc0d1238030743f1196d9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957961"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp、wcscmp、_mbscmp、_mbscmp_l

比较字符串。

> [!IMPORTANT]
> **_mbscmp**和 **_mbscmp_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*string1*、 *string2*<br/>
要比较的 null 终止的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个函数的返回值指示*string1*与*string2*的序号关系。

|值|string1 与 string2 的关系|
|-----------|----------------------------------------|
|< 0|*string1*小于*string2*|
|0|*string1*与*string2*相同|
|> 0|*string1*大于*string2*|

参数验证错误时， **_mbscmp**和 **_mbscmp_l**返回 **_NLSCMPERROR**，后者在 string .h > \<和\<mbstring.h > 中定义。

## <a name="remarks"></a>备注

**Strcmp**函数执行*string1*和*string2*的序号比较，并返回一个指示它们关系的值。 **wcscmp**和 **_mbscmp**分别为**strcmp**的宽字符和多字节字符版本。 **_mbscmp**根据当前的多字节代码页识别多字节字符序列，并在发生错误时返回 **_NLSCMPERROR** 。 **_mbscmp_l**具有相同的行为，但使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 此外，如果*string1*或*string2*是 null 指针， **_mbscmp**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则 **_mbscmp**和 **_mbscmp_l**返回 **_NLSCMPERROR** ，并将**errno**设置为**EINVAL**。 **strcmp**和**wcscmp**不会验证其参数。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp**函数不同于**strcoll**函数，因为**strcmp**比较是序号，不受区域设置的影响。 **strcoll**使用当前区域设置的**LC_COLLATE**类别对字符串按字典顺序进行比较。 有关**LC_COLLATE**类别的详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。

在“C”区域设置中，字符集 (ASCII 字符集) 中的字符顺序与字典中的字符顺序一样。 但是在其他区域设置中，字符集中的字符顺序可能与字典中的顺序不同。 例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“ä”（值 0xE4）之前，但在字典顺序中，字符“ä”位于字符“a”之前。

在字符集和字典字符顺序不同的区域设置中，可以使用**strcoll**而不是**strcmp**来比较字符串的字典。 或者，可以对原始字符串使用**strxfrm** ，然后对生成的字符串使用**strcmp** 。

**Strcmp**函数区分大小写。 stricmp、 **wcsicmp和\_** **mbsicmp通过首先将字符串转换为\_** 其小写形式来比较字符串。  **\_** 包含位于 ASCII 表中的 "Z" 和 "a" 之间的两个字符串（"["、"\\"、"]"、"^"、"_" 和 "\`"）的比较方式不同，具体取决于它们的大小写。 例如，如果比较采用小写形式（"abcde...z" > "abcd ^"），则两个字符串 "ABCDE...Z" 和 "ABCD ^" 比较一种方式（如果比较结果为大写，则为 "ABCDE...Z" < "ABCD ^"）。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> 或 \<wchar.h>|
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
