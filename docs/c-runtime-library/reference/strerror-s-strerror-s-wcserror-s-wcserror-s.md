---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 11/04/2016
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 00ff9d0df1a78d07eaa509201fb998b30396cc4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429635"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

获取系统错误信息 (**strerror_s**， **_wcserror_s**) 或打印用户提供的错误消息 (**_strerror_s**， **__wcserror_s**). 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) 具有安全性增强功能。

## <a name="syntax"></a>语法

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>参数

*buffer*<br/>
要保存错误字符串的缓冲区。

*numberOfElements*<br/>
缓冲区的大小。

*errnum*<br/>
错误号。

*strErrMsg*<br/>
用户提供的消息。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

### <a name="error-condtions"></a>错误条件

|*buffer*|*numberOfElements*|*strErrMsg*|内容*缓冲区*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|任何|任何|n/a|
|任何|0|任何|未修改|

## <a name="remarks"></a>备注

**Strerror_s**函数映射*errnum*到错误消息字符串，并返回中的字符串*缓冲区*。 **_strerror_s**不采用错误编号; 它使用的当前值**errno**以确定相应的消息。 既不**strerror_s**也不 **_strerror_s**实际打印的消息： 需要为此，请调用输出函数，如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*是**NULL**， **_strerror_s**返回的字符串*缓冲区*包含最后一个库调用的系统错误消息生成了错误的。 错误消息字符串以换行符 ('\n') 结尾。 如果*strErrMsg*不等于**NULL**，然后 **_strerror_s**返回的字符串*缓冲区*（按顺序） 包含你的字符串消息，冒号、 空格、 生成错误，并换行字符的最后一个库调用的系统错误消息。 你的字符串消息长度最多可达 94 个字符。

如果长度超出了这些函数将截断错误消息*numberOfElements* -1。 中的结果字符串*缓冲区*始终 null 值结束。

有关的实际错误编号 **_strerror_s**存储在变量[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 **_strerror_s**通过使用来访问相应的错误消息**errno**为该变量的索引值 **_sys_errlist**。 变量的值[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)定义为中的元素的最大数 **_sys_errlist**数组。 若要生成准确的结果，调用 **_strerror_s**后立即在库例程将返回错误消息。 否则为后续调用**strerror_s**或 **_strerror_s**可以覆盖**errno**值。

**_wcserror_s**并 **__wcserror_s**宽字符版本的**strerror_s**并 **_strerror_s**分别。

这些函数验证其参数。 如果缓冲区**NULL**或者如果大小参数为 0，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数返回**EINVAL**并设置**errno**到**EINVAL**。

**_strerror_s**， **_wcserror_s**，和 **__wcserror_s**不是 ANSI 定义的一部分，而是其 Microsoft 扩展。 不要使用它们在需要时可移植性;对于 ANSI 兼容性，使用**strerror_s**相反。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strerror_s**， **_strerror_s**|\<string.h>|
|**_wcserror_s**， **__wcserror_s**|\<string.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [perror](perror-wperror.md) 示例。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
