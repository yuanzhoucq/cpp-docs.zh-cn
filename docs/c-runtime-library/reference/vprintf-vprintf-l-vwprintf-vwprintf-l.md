---
title: vprintf、_vprintf_l、vwprintf、_vwprintf_l
ms.date: 11/04/2016
apiname:
- vprintf
- _vwprintf_l
- _vprintf_l
- vwprintf
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
- vwprintf
- _vtprintf
helpviewer_keywords:
- vwprintf function
- _vwprintf_l function
- vwprintf_l function
- _vtprintf function
- vtprintf_l function
- vprintf function
- _vprintf_l function
- vprintf_l function
- vtprintf function
- _vtprintf_l function
- formatted text [C++]
ms.assetid: 44549505-00a0-4fa7-9a85-f2e666f55a38
ms.openlocfilehash: db984b822e8b496d63bf7844882676581562930d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499132"
---
# <a name="vprintf-_vprintf_l-vwprintf-_vwprintf_l"></a>vprintf、_vprintf_l、vwprintf、_vwprintf_l

使用指向参数列表的指针编写格式化输出。 提供这些函数的更多安全版本；请参阅 [vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)。

## <a name="syntax"></a>语法

```C
int vprintf(
   const char *format,
   va_list argptr
);
int _vprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int vwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>参数

*format*<br/>
格式规范。

*argptr*<br/>
指向参数列表的指针。

*locale*<br/>
要使用的区域设置。

有关更多信息，请参见 [格式规范](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>返回值

**vprintf**和**vwprintf**返回写入的字符数, 不包括终止 null 字符, 或在出现输出错误时返回一个负值。 如果*format*为空指针, 或如果格式字符串包含无效的格式字符, 则将调用无效的参数处理程序, 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则函数将返回-1, 并将**errno**设置为**EINVAL**。

有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数都采用一个指向参数列表的指针, 然后将给定数据格式化并写入**stdout**。

**vwprintf**是**vprintf**的宽字符版本;如果在 ANSI 模式下打开流, 则这两个函数的行为相同。 **vprintf**当前不支持输出到 UNICODE 流中。

这些带有 **_l**后缀的函数的版本相同, 只不过它们使用传入的区域设置参数而不是当前线程区域设置。

> [!IMPORTANT]
> 确保 format不是用户定义的字符串。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。 请注意，已检测到无效格式字符串并发生错误。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf**|**vprintf**|**vprintf**|**vwprintf**|
|**_vtprintf_l**|**_vprintf_l**|**_vprintf_l**|**_vwprintf_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**vprintf**、 **_vprintf_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**vwprintf**、 **_vwprintf_l**|\<stdio.h> 或 \<wchar.h> 和 \<stdarg.h>|\<varargs.h>*|

\* 仅对 UNIX V 兼容性是必需的。

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout**和**stderr**关联的标准流句柄必须重定向, 然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函数](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
