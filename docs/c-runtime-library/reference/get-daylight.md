---
title: _get_daylight
ms.date: 11/04/2016
apiname:
- __daylight
- _get_daylight
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 03c3386e59379f460d3c07dc310153d990c02b05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332305"
---
# <a name="getdaylight"></a>_get_daylight

检索夏令时偏移量（以小时为单位）。

## <a name="syntax"></a>语法

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>参数

*小时数*<br/>
夏令时偏移量（以小时为单位）。

## <a name="return-value"></a>返回值

如果成功，则将为零; **errno**如果发生错误，则值。

## <a name="remarks"></a>备注

**_Get_daylight**函数检索的夏时制为整数小时数。 如果夏令时有效，则默认偏移量为一小时（但是少数地区遵守两小时的偏移量）。

如果*小时*是**NULL**，如中所述，将调用无效的参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

我们建议你使用此函数而不是宏 **_daylight**或不推荐使用的函数 **__daylight**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
