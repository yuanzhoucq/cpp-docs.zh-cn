---
title: _RTC_SetErrorFunc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs:
- C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3d83690ceed2fec75da266d409e8323bc057028
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

将函数指定为报告运行时错误检查 (RTC) 的处理程序。 此函数已弃用;使用 **_RTC_SetErrorFuncW**相反。

## <a name="syntax"></a>语法

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>参数

*函数*<br/>
处理运行时错误检查的函数的地址。

## <a name="return-value"></a>返回值

以前定义的错误函数。 如果没有以前定义的函数，则返回 NULL。

## <a name="remarks"></a>备注

不要使用此功能;请改用 **_RTC_SetErrorFuncW**。 仅为后向兼容性保留使用此函数。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
