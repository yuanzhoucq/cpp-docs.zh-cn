---
title: getc、getwc
ms.date: 4/2/2020
api_name:
- getwc
- getc
- _o_getc
- _o_getwc
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
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: 5c05d7a2743cd0c1e843d6895e8f5574031ab098
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344837"
---
# <a name="getc-getwc"></a>getc、getwc

从流中读取字符。

## <a name="syntax"></a>语法

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*流*<br/>
输入流。

## <a name="return-value"></a>返回值

返回读取的字符。 要指示读取错误或文件结尾条件 **，getc**返回**EOF** **，getwc**返回**WEOF**。 对于**getc，** 使用**ferror**或**feof**检查错误或文件结尾。 如果*流*为**NULL，getc**和**getwc**将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 **NULL** 如果允许执行继续，这些函数返回**EOF（** 或**GETwc**的**WEOF），** 并将**errno**设置为**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个例程从文件的当前位置读取单个字符，并增量关联的文件指针（如果已定义）以指向下一个字符。 该文件与*流*相关联。

这些函数会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 [_getc_nolock、_getwc_nolock](getc-nolock-getwc-nolock.md)。

下面是例程特定的备注。

|例程|备注|
|-------------|-------------|
|**getc**|与**fgetc**相同，但作为函数和宏实现。|
|**getwc**|宽字符版本的**getc**。 根据*流*是在文本模式还是二进制模式下打开，读取多字节字符或宽字符。|

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crt_getctxt"></a>输入：crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>输出

```Output
Input was: Line one.
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
[ungetc、ungetwc](ungetc-ungetwc.md)<br/>
