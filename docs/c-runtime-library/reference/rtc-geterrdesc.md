---
title: _RTC_GetErrDesc | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7154f6de192ee6b681ed0419126f3d4b682abb8c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451340"
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc

返回运行时错误检查 (RTC) 类型的简要描述。

## <a name="syntax"></a>语法

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>参数

*errnum*<br/>
一个数字，介于 0 和 **_RTC_NumErrors** 返回的值减 1 所得的值之间。

## <a name="return-value"></a>返回值

一个字符串，其中包含由运行时错误检查系统检测到的一个错误类型的简短描述。 如果错误小于零或大于或等于返回的值[_RTC_NumErrors](rtc-numerrors.md)， **_RTC_GetErrDesc**返回**NULL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[运行时错误检查](../../c-runtime-library/run-time-error-checking.md)<br/>
