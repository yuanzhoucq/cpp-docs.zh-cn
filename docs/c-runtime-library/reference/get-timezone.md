---
title: _get_timezone
ms.date: 11/04/2016
apiname:
- _get_timezone
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
- _get_timezone
- get_timezone
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
ms.openlocfilehash: 26cf8114ab766bdb394d2db9ad5842622a447bd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613910"
---
# <a name="gettimezone"></a>_get_timezone

检索协调世界时 (UTC) 和当地时间之间的差异（以秒为单位）。

## <a name="syntax"></a>语法

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>参数

*秒*<br/>
UTC 和当地时间之间的差异（以秒为单位）。

## <a name="return-value"></a>返回值

如果成功，则将为零; **errno**如果发生错误，则值。

## <a name="remarks"></a>备注

**_Get_timezone**函数检索 UTC 与当地时间之间的整数以秒为单位差异。 对于太平洋标准时间（比 UTC 时间晚 8 个小时），默认值是 28,800 秒。

如果*秒*是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
