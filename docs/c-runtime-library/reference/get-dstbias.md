---
title: _get_dstbias
ms.date: 4/2/2020
api_name:
- _get_dstbias
- __dstbias
- _o___dstbias
- _o__get_dstbias
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 969b6d2dfd83a1a136fdfb3d17f8f843337b792c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345231"
---
# <a name="_get_dstbias"></a>_get_dstbias

检索夏令时偏移量（以秒为单位）。

## <a name="syntax"></a>语法

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>参数

*秒*<br/>
夏令时偏移量（以秒为单位）。

## <a name="return-value"></a>返回值

如果成功为零，则为**错误**值（如果发生错误）。

## <a name="remarks"></a>备注

**_get_dstbias**函数以整数检索夏令时的秒数。 如果夏令时有效，则默认偏移量为 3600 秒，这也是一个小时包含的秒数（但是少数地区遵守两小时的偏移量）。

如果*秒*为**NULL，** 则无效参数处理程序将调用[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数将**errno**设置到**EINVAL**并返回**EINVAL**。

我们建议您使用此函数，而不是宏 **_dstbias**或弃用函数 **__dstbias**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
