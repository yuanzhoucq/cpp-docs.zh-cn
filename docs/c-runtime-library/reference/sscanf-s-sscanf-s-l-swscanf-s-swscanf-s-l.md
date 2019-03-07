---
title: sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
ms.date: 11/04/2016
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 07911b7254e74c28310669a697c7492b69567b7f
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210895"
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l

从字符串中读取格式化数据。 这些版本的 [sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) 具有安全性增强功能，如 [CRT 的安全性增强功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
存储的数据

*format*<br/>
窗体控件字符串。 有关详细信息，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

*argument*<br/>
可选自变量

*locale*<br/>
要使用的区域设置

## <a name="return-value"></a>返回值

每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 返回值是**EOF**错误或如果在第一个转换之前到达字符串的末尾。

如果*缓冲区*或*格式*是**NULL**调用指针，无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回-1 并设置**errno**到**EINVAL**

有关这些及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Sscanf_s**函数读取来自数据*缓冲区*到每个给定的位置*参数*。 格式字符串之后的参数指定指向具有中的类型说明符相对应的类型的变量的指针*格式*。 与安全级别较低的版本不同[sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md)，使用类型字段字符时，缓冲区大小参数是必需**c**， **C**， **s**，**S**，或字符串中包含的控件集 **[]**。 必须紧跟在需要缓冲区大小的缓冲区参数后提供缓冲区大小（以字符为单位）作为附加参数。 例如，如果你正在读入一个字符串，则将传递该字符串的缓冲区大小，如下所示：

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

缓冲区大小包括终止 null 字符。 可以使用宽度规范字段来确保读入的标记可放入缓冲区中。 如果未使用任何宽度规范字段，并且读取的标记太大以致缓冲区中无法容纳，则不会向该缓冲区写入任何内容。

对于字符，可读取单个字符，如下所示：

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

此示例从输入字符串读取单个字符，然后将其存储在宽字符缓冲区中。 在读取非 null 终止的字符串的多个字符时，将无符号整数用作宽度规范和缓冲区大小。

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

有关详细信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 类型字段字符](../../c-runtime-library/scanf-type-field-characters.md)。

> [!NOTE]
> 大小参数的类型是**无符号**，而非**size_t**。 当针对 64 位目标进行编译，使用静态强制转换来转换 **_countof**或**sizeof**结果为正确的大小。

*格式*参数控制字段输入的解释，并且具有相同格式和函数作为*格式*参数**scanf_s**函数。 如果在重叠的字符串之间发生复制，则此行为不确定。

**swscanf_s**是宽字符版本**sscanf_s**; 的自变量**swscanf_s**都是宽字符字符串。 **sscanf_s**不处理多字节十六进制字符。 **swscanf_s**不处理 Unicode 全角十六进制或"兼容区"字符。 否则为**swscanf_s**并**sscanf_s**行为方式相同。

具有这些函数的版本 **_l**后缀完全相同，只不过它们使用传入的区域设置参数而不是当前线程区域设置。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**sscanf_s**， **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**， **_swscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
