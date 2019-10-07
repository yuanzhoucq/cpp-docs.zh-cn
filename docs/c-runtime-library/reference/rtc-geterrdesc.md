---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
api_name:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: 7174e9242b77a904df817886df4f8c763e3e0b2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949059"
---
# <a name="_rtc_geterrdesc"></a>_RTC_GetErrDesc

返回运行时错误检查 (RTC) 类型的简要描述。

## <a name="syntax"></a>语法

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>参数

*errnum*<br/>
一个数字，介于 0 和 **_RTC_NumErrors**返回的值减 1 所得的值之间。

## <a name="return-value"></a>返回值

一个字符串，其中包含由运行时错误检查系统检测到的一个错误类型的简短描述。 如果错误小于零或大于或等于[_RTC_NumErrors](rtc-numerrors.md)返回的值，则 **_RTC_GetErrDesc**将返回**NULL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
