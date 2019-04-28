---
title: _get_dstbias
ms.date: 11/04/2016
apiname:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 61807f854dc9c2f7de6f0acd5bbf4668987ce49e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332372"
---
# <a name="getdstbias"></a>_get_dstbias

检索夏令时偏移量（以秒为单位）。

## <a name="syntax"></a>语法

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>参数

*seconds*<br/>
夏令时偏移量（以秒为单位）。

## <a name="return-value"></a>返回值

如果成功，则将为零; **errno**如果发生错误，则值。

## <a name="remarks"></a>备注

**_Get_dstbias**函数检索中夏时制整数形式的秒数。 如果夏令时有效，则默认偏移量为 3600 秒，这也是一个小时包含的秒数（但是少数地区遵守两小时的偏移量）。

如果*秒*是**NULL**，如中所述，将调用无效的参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

我们建议你使用此函数而不是宏 **_dstbias**或不推荐使用的函数 **__dstbias**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
