---
title: sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l
ms.date: 11/04/2016
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
apitype: DLLExport
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: 875cd5eca56511c2b421584766584c0c974cd775
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521864"
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l

将设置格式的数据写入字符串。 可提供某些函数的更多安全版本，请参阅 [sprintf_s、_sprintf_s_l、swprintf_s 和 _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。 安全版本的**swprintf**并 **_swprintf_l**不会*计数*参数。

## <a name="syntax"></a>语法

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
输出的存储位置

*count*<br/>
要存储在 Unicode 版的此函数中的最大字符数。

*format*<br/>
格式控件字符串

*自变量*<br/>
可选自变量

*locale*<br/>
要使用的区域设置。

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>返回值

写入的字符数或为-1 时出错。 如果*缓冲区*或*格式*是 null 指针，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回-1 并设置**errno**到**EINVAL**。

**sprintf**返回存储中的字节数*缓冲区*，不包括终止 null 字符。 **swprintf**返回存储在中的宽字符数*缓冲区*，不包括终止 null 宽字符。

## <a name="remarks"></a>备注

**Sprintf**函数设置的格式并将存储一系列字符和中的值*缓冲区*。 每个*自变量*（如果有） 进行转换和输出中的相应格式规范根据*格式*。 该格式包括普通字符，其形式和函数与相同*格式*参数[printf](printf-printf-l-wprintf-wprintf-l.md)。 null 字符追加在写入的最后一个字符后。 如果在重叠的字符串之间发生复制，则此行为不确定。

> [!IMPORTANT]
> 使用**sprintf**，没有方法来限制写入的字符数，这意味着，使用代码**sprintf**容易受到缓冲区溢出。 请考虑使用相关的函数[_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)，它指定要写入的字符最大数目*缓冲区*，或使用[_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md)来确定大小缓冲区是必需的。 此外，确保*格式*不是用户定义的字符串。

**swprintf**是宽字符版本**sprintf**; 的指针参数**swprintf**都是宽字符字符串。 检测到的编码中的错误**swprintf**可能有所不同，在**sprintf**。 **swprintf**并**fwprintf**行为方式相同，只不过**swprintf**将输出写入到一个字符串，而不是类型的目标**文件**，和**swprintf**要求*计数*参数来指定要写入的字符的最大数。 使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前线程区域设置的区域设置参数。

**swprintf**符合 ISO C 标准，这要求第二个参数，*计数*，类型的**size_t**。 若要强制旧的非标准行为，定义 **_CRT_NON_CONFORMING_SWPRINTFS**。 在未来版本中，可能会删除旧行为，因此应将代码更改为使用新的符合标准行为。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**sprintf**， **_sprintf_l**|\<stdio.h>|
|**swprintf**， **_swprintf_l**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
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
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
