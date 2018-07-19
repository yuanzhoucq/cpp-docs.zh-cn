---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 362716963911a29a9b3558c387e69c4cd91b369e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415577"
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

**Strerror_s**函数映射*errnum*为错误消息字符串，返回中的字符串*缓冲区*。 **_strerror_s**不带错误号; 它使用的当前值**errno**来确定适当的消息。 既不**strerror_s**也不 **_strerror_s**实际输出的消息： 需要为此，调用输出函数，如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

如果*strErrMsg*是**NULL**， **_strerror_s**返回中的字符串*缓冲区*包含最后一次库调用的系统错误消息产生错误。 错误消息字符串以换行符 ('\n') 结尾。 如果*strErrMsg*是否不等于**NULL**，然后 **_strerror_s**返回中的字符串*缓冲区*（按顺序） 包含你的字符串消息，冒号、 一个空格、 产生错误，并换行字符的最后一个库调用的系统错误消息。 你的字符串消息长度最多可达 94 个字符。

这些函数将截断的错误消息，如果其长度超过*numberOfElements* -1。 在生成的字符串*缓冲区*始终以 null 结尾。

实际错误数 **_strerror_s**变量中存储[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 通过变量 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 访问系统错误消息，该变量是按错误编号排序的消息数组。 **_strerror_s**使用访问相应的错误消息**errno**为变量的索引值 **_sys_errlist**。 变量的值[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)定义中的元素的最大数目为 **_sys_errlist**数组。 若要生成准确的结果，调用 **_strerror_s**库例程返回错误后立即。 否则为因为在后续调用**strerror_s**或 **_strerror_s**可以覆盖**errno**值。

**_wcserror_s**和 **__wcserror_s**宽字符版本的**strerror_s**和 **_strerror_s**分别。

这些函数验证其参数。 如果缓冲区已**NULL**或如果大小参数为 0，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回**EINVAL**并设置**errno**到**EINVAL**。

**_strerror_s**， **_wcserror_s**，和 **__wcserror_s**不是 ANSI 定义的一部分而是改为 Microsoft 扩展。 不要使用它们需要可移植性;对于 ANSI 兼容性，使用**strerror_s**相反。

在 C++ 中，通过模板重载简化这些函数的使用；重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试版本首先用 0xFD 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
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
