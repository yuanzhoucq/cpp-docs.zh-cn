---
title: strerror、_strerror、_wcserror、__wcserror
description: 描述 Microsoft C 运行时库 （CRT） 功能，_strerror、_wcserror和__wcserror。
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337331"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror、_strerror、_wcserror、__wcserror

获取系统错误消息字符串 **（strerror、_wcserror）** 或设置用户提供的错误消息字符串 **（_strerror，__wcserror）** 的格式 **__wcserror**。 **_wcserror** 这些函数的更安全版本已经发布，请参阅 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

## <a name="syntax"></a>语法

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>参数

*厄勒纳姆*\
错误号。

*斯特雷姆斯格*\
用户提供的消息。

## <a name="return-value"></a>返回值

所有这些函数都返回指向错误消息字符串的指针，该指针位于运行时拥有的线程本地存储缓冲区中。 以后对同一线程的调用可以覆盖此字符串。

## <a name="remarks"></a>备注

**strerror**函数将*errnum*映射到错误消息字符串，并返回指向该字符串的指针。 **strerror**和 **_strerror**函数实际上不会打印消息。 要打印，请调用输出函数，如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果*strErrMsg*作为**NULL**传递 **，_strerror**返回指向字符串的指针。 它包含生成错误的最后一个库调用的系统错误消息。 错误消息字符串以换行符 ('\n') 结尾。 当*strErrMsg*不是**NULL**时，字符串按顺序包含 *：strErrMsg*字符串、冒号、空格、系统错误消息和一个 newline 字符。 您的字符串消息最多可以是 94 个字符，以窄 （**_strerror**） 或宽 （**__wcserror**） 字符。

**_strerror**的实际错误编号存储在变量[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 要生成准确的结果，请立即在库例程返回错误后调用 **_strerror。** 否则，以后对库例程的调用可能会覆盖**errno**值。

**_wcserror**和 **__wcserror**分别是大字符版本的**strerror**和 **_strerror。**

**_strerror、_wcserror**和 **__wcserror**是特定于 Microsoft 的，而不是标准 C 库的一部分。 **_wcserror** 我们不建议您在需要便携式代码的地方使用它们。 对于标准 C 兼容性，请使用**strerror。**

要获取错误字符串，我们建议 **_wcserror****而不是弃**用的宏[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和[_sys_nerr，](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)弃用的内部函数 **__sys_errlist**和 **__sys_nerr**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>通用文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**， **__wcserror**|\<string.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [perror](perror-wperror.md) 示例。

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)\
[更清晰](clearerr.md)\
[费雷尔](ferror.md)\
[perror、_wperror](perror-wperror.md)
