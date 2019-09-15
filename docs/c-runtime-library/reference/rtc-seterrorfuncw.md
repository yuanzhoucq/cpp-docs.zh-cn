---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 0d45e5c857e917ca23b62482c64a06314565226e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948969"
---
# <a name="_rtc_seterrorfuncw"></a>_RTC_SetErrorFuncW

将函数指定为报告运行时错误检查 (RTC) 的处理程序。

## <a name="syntax"></a>语法

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>参数

*函数*<br/>
处理运行时错误检查的函数的地址。

## <a name="return-value"></a>返回值

以前定义的错误函数;如果没有以前定义的函数，则**为 NULL** 。

## <a name="remarks"></a>备注

在新代码中，仅使用 **_RTC_SetErrorFuncW**。 **_RTC_SetErrorFunc**仅包含在库中，以便向后兼容。

**_RTC_SetErrorFuncW**回调仅适用于它链接的组件，但不是全局的。

请确保传递给 **_RTC_SetErrorFuncW**的地址是有效的错误处理函数的地址。

如果使用[_RTC_SetErrorType](rtc-seterrortype.md)为错误分配了类型-1，则不会调用错误处理函数。

在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数。 有关更多信息，请参见 [Using Run-Time Checks Without the C Run-Time Library](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

**_RTC_error_fnW** 定义如下：

```cpp
typedef int (__cdecl * _RTC_error_fnW)(
    int errorType,
    const wchar_t * filename,
    int linenumber,
    const wchar_t * moduleName,
    const wchar_t * format,
    ... );
```

其中：

*errorType*<br/>
由 [_RTC_SetErrorType](rtc-seterrortype.md)指定的错误类型。

*filename*<br/>
为发生故障的源文件，或者，如果没有调试信息，则为 null。

*linenumber*<br/>
为其中发生故障的 *filename* 中的行，或者，如果没有调试信息，则为 0。

*moduleName*<br/>
DLL 或发生故障的可执行文件的名称。

*format*<br/>
要使用剩余的参数显示错误消息的 printf 样式字符串。 VA_ARGLIST 的第一个自变量是出现的 RTC 错误号。

有关演示如何使用 **_RTC_error_fnW** 的示例，请参阅[本机运行时检查自定义](/visualstudio/debugger/native-run-time-checks-customization)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
