---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 4/2/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337369"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

获取系统错误消息 **（strerror_s，_wcserror_s）** 或打印用户提供的错误消息 **（_strerror_s** **，__wcserror_s）。** **_wcserror_s** 如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述，这些版本的 [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) 具有安全性增强功能。

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

*缓冲区*<br/>
要保存错误字符串的缓冲区。

*元素数*<br/>
缓冲区的大小。

*厄勒纳姆*<br/>
错误号。

*斯特雷姆斯格*<br/>
用户提供的消息。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

### <a name="error-condtions"></a>错误条件

|*缓冲区*|*元素数*|*斯特雷姆斯格*|*缓冲区*的内容|
|--------------|------------------------|-----------------|--------------------------|
|**空**|any|any|不适用|
|any|0|any|未修改|

## <a name="remarks"></a>备注

**strerror_s**函数将*errnum*映射到错误消息字符串，返回*缓冲区*中的字符串 。 **_strerror_s**不采用错误编号;因此，_strerror_s 不会采用错误编号。它使用**errno**的当前值来确定适当的消息。 **strerror_s_strerror_s**实际上**都没有**打印消息：为此，您需要调用输出函数，如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*为**NULL，_strerror_s**返回*缓冲区*中的字符串，其中包含生成错误的最后一个库调用的系统错误消息。 **_strerror_s** 错误消息字符串以换行符 ('\n') 结尾。 如果*strErrMsg*不等于**NULL，** 则 **_strerror_s**返回*缓冲区*中的字符串，其中包含（顺序）字符串消息、冒号、空格、最后一个生成错误的库调用的系统错误消息以及换行符。 你的字符串消息长度最多可达 94 个字符。

如果错误消息的长度超过*元素数*-1，则这些函数会截截错误消息。 *缓冲区*中生成的字符串始终为空终止。

**_strerror_s**的实际误差号存储在变量[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 **_strerror_s**使用**errno**值作为变量 **_sys_errlist**的索引来访问相应的错误消息。 变量[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的值定义为 **_sys_errlist**数组中元素的最大数量。 要生成准确的结果，请立即在库例程返回错误后调用 **_strerror_s。** 否则，对**strerror_s**或 **_strerror_s**的后续调用可能会覆盖**errno**值。

**_wcserror_s**和 **__wcserror_s**分别是**strerror_s**和 **_strerror_s**的宽字符版本。

这些函数验证其参数。 如果缓冲区为**NULL**或大小参数为 0，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回**EINVAL**并将**errno**设置为**EINVAL**。

**_strerror_s、_wcserror_s**和 **__wcserror_s**不是 ANSI 定义的一部分，而是微软对它扩展。 **_wcserror_s** 请勿在需要便携性的地方使用它们;对于 ANSI 兼容性，请使用**strerror_s。**

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strerror_s**， **_strerror_s**|\<string.h>|
|**_wcserror_s**， **__wcserror_s**|\<string.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [perror](perror-wperror.md) 示例。

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
