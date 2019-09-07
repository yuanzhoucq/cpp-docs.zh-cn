---
title: _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l
ms.date: 11/04/2016
apiname:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
ms.openlocfilehash: 3652587c9622c2eb9fe316782d1b1c7c9644dc8f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739834"
---
# <a name="_cprintf_s-_cprintf_s_l-_cwprintf_s-_cwprintf_s_l"></a>_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l

格式化并打印到控制台。 这些版本的 [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _cprintf_s(
   const char * format [,
   argument] ...
);
int _cprintf_s_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_s(
   const wchar * format [,
   argument] ...
);
int _cwprintf_s_l(
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

打印的字符数。

## <a name="remarks"></a>备注

这些函数将一系列字符和值直接格式化并输出到控制台，并使用 **_putch**函数（ **_putwch** for **_cwprintf_s**）来输出字符。 每个*自变量*（如果有）根据*格式*规范的相应格式规范进行转换和输出。 格式具有与[printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)函数的*format*参数相同的形式和函数。 与**fprintf_s**、 **printf_s**和**sprintf_s**函数不同，在输出时， **_cprintf_s**和 **_cwprintf_s**都不会将换行符转换为回车换行符（CR-LF）组合。

一个重要的区别在于，在 Windows NT 中使用时， **_cwprintf_s**会显示 Unicode 字符。 与 **_cprintf_s**不同， **_cwprintf_s**使用当前的控制台区域设置

使用 **_l**后缀的这些函数的版本是相同的，只不过它们使用传入的区域设置参数而不是当前区域设置。

> [!IMPORTANT]
> 确保 format不是用户定义的字符串。

与不安全版本一样（请参阅[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)），这些函数将验证其参数并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，如果*format*为 null变为. 这些函数与不安全版本的不同之处在于，格式字符串本身也需进行验证。 如果有任何未知或格式错误的格式化说明符，则这些函数将调用无效参数处理程序。 在所有情况下，如果允许执行继续，则函数将返回-1，并将**errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_cprintf_s**、 **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**、 **_cwprintf_s_l**|\<conio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_cprintf_s.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
   int      i = -16, h = 29;
   unsigned u = 62511;
   char     c = 'A';
   char     s[] = "Test";

   /* Note that console output does not translate \n as
    * standard output does. Use \r\n instead.
    */
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)<br/>
[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
