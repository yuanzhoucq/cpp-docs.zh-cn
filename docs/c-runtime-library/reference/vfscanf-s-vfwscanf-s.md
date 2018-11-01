---
title: vfscanf_s、vfwscanf_s
ms.date: 11/04/2016
apiname:
- vfscanf_s
- vfwscanf_s
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
apitype: DLLExport
f1_keywords:
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
ms.openlocfilehash: 40bfad26ebdf7ffba48a184491a371f4010e90ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429401"
---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s、vfwscanf_s

从流中读取格式化数据。 这些 vfscanf、vfwscanf 版本具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。

## <a name="syntax"></a>语法

```C
int vfscanf_s(
   FILE *stream,
   const char *format,
   va_list arglist
);
int vfwscanf_s(
   FILE *stream,
   const wchar_t *format,
   va_list arglist
);

```

### <a name="parameters"></a>参数

*流*<br/>
指向**文件**结构的指针。

*format*<br/>
窗体控件字符串。

*arglist*<br/>
变量参数列表。

## <a name="return-value"></a>返回值

每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果发生错误，或如果在第一次转换前达到文件流的末尾，则返回值是**EOF**有关**vfscanf_s**并**vfwscanf_s**。

这些函数验证其参数。 如果*流*是无效文件指针，或*格式*是 null 指针，这些函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回**EOF**并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**Vfscanf_s**函数将从当前的位置读取数据*流*到由给定的位置*arglist*参数列表 （如果有）。 列表中的每个参数必须是指向类型中的类型说明符相对应的变量的指针*格式*。 *格式*控制字段输入的解释，并且具有相同格式和函数作为*格式*自变量**scanf_s**; 请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)有关的说明*格式*。 **vfwscanf_s**是宽字符版本**vfscanf_s**; 的格式参数**vfwscanf_s**是宽字符字符串。 如果在 ANSI 模式下打开流，则这些函数行为相同。 **vfscanf_s**当前不支持 UNICODE 流的输入。

更安全的函数之间的主要区别 (具有 **_s**后缀) 和其他版本是更安全的函数需要在每个字符的大小**c**， **C**， **s**， **S**，并且 **[** 类型字段以作为紧跟变量参数传递。 有关详细信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。

> [!NOTE]
> 大小参数的类型是**无符号**，而非**size_t**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_vfscanf_s.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf_s to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

FILE *stream;

int call_vfscanf_s(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf_s(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)
    {
        printf("The file vfscanf_s.out was not opened\n");
    }
    else
    {
        fprintf(stream, "%s %ld %f%c", "a-string",
            65000, 3.14159, 'x');
        // Security caution!
        // Beware loading data from a file without confirming its size,
        // as it may lead to a buffer overrun situation.

        // Set pointer to beginning of file:
        fseek(stream, 0L, SEEK_SET);

        // Read data back from file:
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);

        // Output data read:
        printf("%s\n", s);
        printf("%ld\n", l);
        printf("%f\n", fp);
        printf("%c\n", c);

        fclose(stream);
    }
}

```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf、vfwscanf](vfscanf-vfwscanf.md)<br/>
