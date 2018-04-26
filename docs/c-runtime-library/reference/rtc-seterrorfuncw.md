---
title: _RTC_SetErrorFuncW | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1eb3b8e5f6fb602675538c6588372b87df8781ac
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW

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

以前定义的错误函数;或**NULL**如果没有以前定义的函数。

## <a name="remarks"></a>备注

在新代码，仅使用 **_RTC_SetErrorFuncW**。 **_RTC_SetErrorFunc**仅包含在库中的向后兼容性。

**_RTC_SetErrorFuncW**回调仅适用于它在中，链接组件但不是全局。

请确保传递到的地址 **_RTC_SetErrorFuncW**是有效的错误处理函数。

如果错误已被分配为-1 的类型使用[_RTC_SetErrorType](rtc-seterrortype.md)，就会失败的错误处理函数。

在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数。 有关更多信息，请参见 [Using Run-Time Checks Without the C Run-Time Library](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

**_RTC_error_fnW** 定义如下：

> **typedef int (__cdecl \*_RTC_error_fnW) (int** *errorType* **，const wchar_t \***  *filename* **，int***linenumber* **，const wchar_t \***  *moduleName* **，const wchar_t \*** *格式* **，...);** 

其中：

*errorType*由指定的错误类型的[_RTC_SetErrorType](rtc-seterrortype.md)。

*filename*发生故障的源文件或如果没有调试信息则为 null。

*linenumber*中的行*filename*发生故障或如果没有调试信息，则为 0。

*moduleName* DLL 或发生故障的可执行文件名称。

*格式*要显示错误消息，使用剩余的参数的 printf 样式字符串。 VA_ARGLIST 的第一个参数是出现的 RTC 错误号。

有关演示如何使用 **_RTC_error_fnW** 的示例，请参阅[本机运行时检查自定义](/visualstudio/debugger/native-run-time-checks-customization)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
