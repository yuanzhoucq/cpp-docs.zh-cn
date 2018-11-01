---
title: strncmp、wcsncmp、_mbsncmp、_mbsncmp_l
ms.date: 11/04/2016
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
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
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: b8b5472289bacc940bb0cbea7876f246243660bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523747"
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp、wcsncmp、_mbsncmp、_mbsncmp_l

比较高达两个字符串指定数量的字符。

> [!IMPORTANT]
> **_mbsncmp**并 **_mbsncmp_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>参数

*string1*， *string2*<br/>
要比较的字符串。

*count*<br/>
要比较的字符数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值表示的子字符串的关系*string1*并*string2* ，如下所示。

|返回值|描述|
|------------------|-----------------|
|< 0|*string1*的子字符串小于*string2*子字符串|
|0|*string1*子字符串等于*string2*子字符串|
|> 0|*string1*子字符串大于*string2*子字符串|

参数验证错误时， **_mbsncmp**并 **_mbsncmp_l**返回 **_NLSCMPERROR**，其定义中\<string.h > 和\<值 >。

## <a name="remarks"></a>备注

**Strncmp**函数执行的最多前的序号比较*计数*中的字符*string1*并*string2*和返回一个值，该值指示子字符串之间的关系。 **strncmp**是区分大小写的版本 **_strnicmp**。 **wcsncmp**并 **_mbsncmp**区分大小写版本的 **_wcsnicmp**并 **_mbsnicmp**。

**wcsncmp**并 **_mbsncmp**宽字符及多字节字符版本的**strncmp**。 参数**wcsncmp**是宽字符字符串; **_mbsncmp**是多字节字符字符串。 **_mbsncmp**根据多字节代码页识别多字节字符序列，并返回 **_NLSCMPERROR**发生错误时。

此外， **_mbsncmp**并 **_mbsncmp_l**验证参数。 如果*string1*或*string2*是 null 指针，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则 **_mbsncmp**并 **_mbsncmp_l**返回 **_NLSCMPERROR**并设置**errno**到**EINVAL**。 **strncmp**并**wcsncmp**不会验证其参数。 否则这些函数具有相同行为。

比较行为 **_mbsncmp**并 **_mbsncmp_l**的设置影响**LC_CTYPE**类别设置的区域设置。 这会控制对多字节字符的前导和尾随字节的检测。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 **_Mbsncmp**函数依赖于区域设置的行为使用当前区域设置。 **_Mbsncmp_l**函数是完全相同，只不过它使用*区域设置*参数相反。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。 如果区域设置是单字节，则这些函数的行为等同于**strncmp**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|映射到宏或内联函数|**_mbsncmp**|映射到宏或内联函数|
|**不适用**|**不适用**|**_mbsncmp_l**|**不适用**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> 或 \<wchar.h>|
|**_mbsncmp**， **_mbsncmp_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
