---
title: _daylight、_dstbias、_timezone 和 _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: d8660c7a6677fb8113b91d6d69a21eef9d1d26c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460510"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight、_dstbias、_timezone 和 _tzname

`_daylight`、`_dstbias`、`_timezone` 和 `_tzname` 在某些时间和日期例程中用来调整本地时间。 这些全局变量因安全性更高的函数版本（它们取代了全局变量）而被弃用。

|全局变量|等效函数|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

在 Time.h 中按如下方式声明它们。

## <a name="syntax"></a>语法

```
extern int _daylight; 
extern int _dstbias; 
extern long _timezone; 
extern char *_tzname[2];
```

## <a name="remarks"></a>备注

在调用 `_ftime`、`localtime` 或 `_tzset` 时，`_daylight`、`_dstbias`、`_timezone` 和 `_tzname` 的值由 `TZ` 环境变量的值确定。 如果您未显式设置 `TZ` 的值，则 `_tzname[0]` 和 `_tzname[1]` 将分别包含“PST”和“PDT”的默认设置。  时间操作函数（[_tzset](../c-runtime-library/reference/tzset.md)、[_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md)，和 [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)）尝试通过在操作系统中查询每个变量的默认值来设置 `_daylight`、`_dstbias` 和 `_timezone` 的值。 下表显示了时区全局变量的值。

|变量|“值”|
|--------------|-----------|
|`_daylight`|如果在 `TZ` 中指定或从操作系统确定夏令时 (DST) 时区，则为非零值；否则为 0。 默认值为 1。|
|`_dstbias`|夏令时的偏移量。|
|`_timezone`|协调世界时和本地时间之间的差异（以秒为单位）。 默认值为 28,800。|
|`_tzname[0]`|派生自 `TZ` 环境变量的时区名称。 默认值是“PST”。|
|`_tzname[1]`|派生自 `TZ` 环境变量的 DST 时区名称。 默认值为“PDT”（太平洋夏令时）。|

## <a name="see-also"></a>请参阅

[全局变量](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)