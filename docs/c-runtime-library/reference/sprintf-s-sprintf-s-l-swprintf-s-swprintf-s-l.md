---
title: sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l
ms.date: 11/04/2016
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
ms.openlocfilehash: 4d4bec339caccf9b0843afada4b56b435243dd11
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210882"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l

将设置格式的数据写入字符串。 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 具有安全性增强功能。

## <a name="syntax"></a>语法

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
输出的存储位置

*sizeOfBuffer*<br/>
可存储的最多字符数。

*format*<br/>
格式控件字符串

*...*<br/>
要设置格式的可选参数

*locale*<br/>
要使用的区域设置。

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>返回值

写入的字符数或为-1 时出错。 如果*缓冲区*或*格式*是 null 指针**sprintf_s**并**swprintf_s**返回-1，并设置**errno**到**EINVAL**。

**sprintf_s**返回存储中的字节数*缓冲区*，不包括终止 null 字符。 **swprintf_s**返回存储在中的宽字符数*缓冲区*，不包括终止 null 宽字符。

## <a name="remarks"></a>备注

**Sprintf_s**函数设置的格式并将存储一系列字符和中的值*缓冲区*。 每个*自变量*（如果有） 进行转换和输出中的相应格式规范根据*格式*。 该格式包括普通字符，其形式和函数与相同*格式*参数[printf](printf-printf-l-wprintf-wprintf-l.md)。 null 字符追加在写入的最后一个字符后。 如果在重叠的字符串之间发生复制，则此行为不确定。

之间的一个主要区别**sprintf_s**并[sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)在于**sprintf_s**检查格式字符串中的有效格式设置字符，而[sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)仅检查格式字符串或缓冲区是否**NULL**指针。 如果任一检查失败，将调用无效参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，函数将返回-1 并设置**errno**到**EINVAL**。

之间的其他主要区别**sprintf_s**并[sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)在于**sprintf_s**使用长度参数来以字符为单位指定输出缓冲区的大小。 如果缓冲区太小，格式化文本，包括终止 null，则将缓冲区设置为空字符串由放置在 null 字符*缓冲区*[0]，并调用无效参数处理程序。 与不同 **_snprintf**， **sprintf_s**保证，缓冲区将以 null 终止除非缓冲区大小为零。

**swprintf_s**是宽字符版本**sprintf_s**; 的指针参数**swprintf_s**都是宽字符字符串。 检测到的编码中的错误**swprintf_s**可能有所不同，在**sprintf_s**。 使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前线程区域设置的区域设置参数。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度（不再需要指定大小参数），并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

有新版**sprintf_s**提供更多控制权如果缓冲区太小，则会发生什么情况。 有关更多信息，请参见 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**sprintf_s**， **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio> 或 \<stdio.h>|
|**swprintf_s**， **_swprintf_s_l**|C: \<stdio.h> 或 \<wchar.h><br /><br /> C++: \<cstdio>、\<cwchar>、\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>示例

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
