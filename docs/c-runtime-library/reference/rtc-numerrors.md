---
title: _RTC_NumErrors
ms.date: 11/04/2016
apiname:
- _RTC_NumErrors
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
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: e13f85f2140473d6e971d27abb6012effd36c37c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477189"
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors

返回可由运行时错误检查 (RTC) 检测出的错误总数。 可以将此数字用作 **for** 循环的控件，循环中的每个值都将传递给 [_RTC_GetErrDesc](rtc-geterrdesc.md)。

## <a name="syntax"></a>语法

```C

int _RTC_NumErrors( void );

```

## <a name="return-value"></a>返回值

一个整数，其值表示可以由 Visual C++ 运行时错误检查检测出的错误总数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
