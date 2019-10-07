---
title: _cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l
ms.date: 11/04/2016
api_name:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
ms.openlocfilehash: a02de28a61812147c192495c4794830f85567a10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942649"
---
# <a name="_cprintf_p-_cprintf_p_l-_cwprintf_p-_cwprintf_p_l"></a>_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l

格式化并输出到控制台，并支持格式字符串中的位置参数。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _cprintf_p(
   const char * format [,
   argument] ...
);
int _cprintf_p_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_p(
   const wchar * format [,
   argument] ...
);
int _cwprintf_p_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>参数

*format*<br/>
窗体控件字符串。

*实际*<br/>
可选参数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

打印的字符数或负值（如果出错）。

## <a name="remarks"></a>备注

这些函数将一系列字符和值直接设置为控制台，并使用 **_putch**和 **_putwch**函数输出字符。 每个*自变量*（如果有）根据*格式*规范的相应格式规范进行转换和输出。 格式具有与[printf_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)函数的*format*参数相同的形式和函数。 **_Cprintf_p**和**cprintf_s**之间的区别在于 **_cprintf_p**支持位置参数，这允许指定在格式字符串中使用参数的顺序。 有关详细信息，请参阅 [printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)。

与**fprintf_p**、 **printf_p**和**sprintf_p**函数不同，在输出时， **_cprintf_p**和 **_cwprintf_p**都不会将换行符转换为回车换行符（CR-LF）组合。 一个重要的区别在于，在 Windows NT 中使用时， **_cwprintf_p**会显示 Unicode 字符。 与 **_cprintf_p**不同， **_cwprintf_p**使用当前的控制台区域设置。

使用 **_l**后缀的这些函数的版本是相同的，只不过它们使用传入的区域设置参数而不是当前区域设置。

> [!IMPORTANT]
> 确保 format不是用户定义的字符串。

同样， **_cprintf_s**和 **_cwprintf_s**，它们会验证输入指针和格式字符串。 如果*格式*或*参数*为**NULL**，或者格式字符串包含无效的格式字符，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回-1，并将**errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_p**|**_cprintf_p**|**_cprintf_p**|**_cwprintf_p**|
|**_tcprintf_p_l**|**_cprintf_p_l**|**_cprintf_p_l**|**_cwprintf_p_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_cprintf_p**、 **_cprintf_p_l**|\<conio.h>|
|**_cwprintf_p**、 **_cwprintf_p_l**|\<conio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_cprintf_p.c
// This program displays some variables to the console
// using the _cprintf_p function.

#include <conio.h>

int main( void )
{
    int         i = -16,
                h = 29;
    unsigned    u = 62511;
    char        c = 'A';
    char        s[] = "Test";

    // Note that console output does not translate
    // \n as standard output does. Use \r\n instead.
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",
                h, i, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)<br/>
[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p 位置参数](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
