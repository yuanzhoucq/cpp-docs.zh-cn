---
title: strerror、_strerror、_wcserror、__wcserror
ms.date: 11/04/2016
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
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
ms.openlocfilehash: 0b4d70687bc2f428162d035c80d6bc8525a8fb9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958143"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror、_strerror、_wcserror、__wcserror

获取系统错误消息字符串（**strerror**， **_wcserror**），或设置用户提供的错误消息字符串（ **_strerror**， **__wcserror**）的格式。 这些函数的更安全版本已经发布，请参阅 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md)。

## <a name="syntax"></a>语法

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>参数

*errnum*<br/>
错误号。

*strErrMsg*<br/>
用户提供的消息。

## <a name="return-value"></a>返回值

所有这些函数都将返回指向错误消息字符串的指针。 后续调用可覆盖该字符串。

## <a name="remarks"></a>备注

**Strerror**函数将*errnum*映射到错误消息字符串，并返回指向该字符串的指针。 **Strerror**和 **_strerror**都不会实际打印消息：为此，必须调用输出函数，例如[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)：

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

如果*strErrMsg*传递为**NULL**，则 **_strerror**将返回一个指向字符串的指针，该字符串包含产生错误的最后一个库调用的系统错误消息。 错误消息字符串以换行符 ('\n') 结尾。 如果*strErrMsg*不等于**NULL**，则 **_strerror**将返回一个指向字符串的指针，该字符串包含（按顺序）你的字符串消息、一个冒号、一个空格、产生错误的最后一个库调用的系统错误消息，以及一个换行符字符. 你的字符串消息长度最多可达 94 个字符。

**_Strerror**的实际错误号存储在变量[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)中。 若要生成准确的结果，请在库例程返回错误后立即调用 **_strerror** 。 否则，对**strerror**或 **_strerror**的后续调用可能会覆盖**errno**值。

**_wcserror**和 **__wcserror**分别是**strerror**和 **_strerror**的宽字符版本。

**_strerror**、 **_wcserror**和 **__wcserror**不是 ANSI 定义的一部分;它们是 Microsoft 扩展，我们建议你不要在需要可移植代码的位置使用它们。 对于 ANSI 兼容性，请改用**strerror** 。

若要获取错误字符串，我们建议使用**strerror**或 **_wcserror** ，而不是已弃用的宏[_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)和[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)以及弃用的内部函数 **__sys_errlist**和 **__sys_nerr**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**、 **__wcserror**|\<string.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [perror](perror-wperror.md) 示例。

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
