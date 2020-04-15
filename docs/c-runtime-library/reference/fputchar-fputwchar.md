---
title: _fputchar、_fputwchar
ms.date: 4/2/2020
api_name:
- _fputchar
- _fputwchar
- _o__fputchar
- _o__fputwchar
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
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- _fputchar
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
ms.openlocfilehash: 29d23dcaba75ad87b462a1a87c7a2ad9c8c7298b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346159"
---
# <a name="_fputchar-_fputwchar"></a>_fputchar、_fputwchar

将字符写入 **stdout**。

## <a name="syntax"></a>语法

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>参数

*C*<br/>
要写入的字符。

## <a name="return-value"></a>返回值

其中每个函数都会返回写入的字符。 对于 **_fputchar****_fputchar，EOF**的返回值指示错误。 对于 **_fputwchar****_fputwchar，WEOF**的返回值表示错误。 如果 c 为**NULL，** 则这些函数将生成无效的参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则返回**EOF（** 或**WEOF），** 并将**errno**设置为**EINVAL**。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

这两个函数都编写单个字符*c*以**进行稳占**并根据需要推进指标。 **_fputchar**等效于`fputc( stdout )`。 它也等效于**putchar**，但仅作为函数实现，而不是作为函数和宏实现。 与**fputc**和**putchar**不同，这些函数与ANSI标准不兼容。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fputchar**|\<stdio.h>|
|**_fputwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 （UWP） 应用中不支持该控制台。 在与控制台关联的标准流句柄 （**stdin、** **stdout**和**stder**） 必须重定向，C 运行时函数才能在 UWP 应用中使用它们。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
