---
title: _get_tzname | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_tzname
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
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b49aa404dda6234382ae461459dece64e5996d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="gettzname"></a>_get_tzname

检索时区名称或夏令时标准时区名称 (DST) 的字符串表示形式。

## <a name="syntax"></a>语法

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
字符串长度*timeZoneName*包括 null 结束符。

*timeZoneName*<br/>
具体取决于时区名称或夏时制标准时间区域名称 (DST) 的表示形式的字符字符串的地址*索引*。

*sizeInBytes*<br/>
大小*timeZoneName*字符以字节为单位的字符串。

*index*<br/>
要检索的两个时区名称之一的索引。

## <a name="return-value"></a>返回值

如果成功，则为零否则为**errno**键入值。

如果任一*timeZoneName*是**NULL**，或*sizeInBytes*为零或小于零 （但不是能同时），无效参数处理程序调用时中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|返回值|内容*timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|TZ 名称的大小|**NULL**|0|0 或 1|0|未修改|
|TZ 名称的大小|任何|> 0|0 或 1|0|TZ 名称|
|未修改|**NULL**|> 0|任何|**EINVAL**|未修改|
|未修改|任何|零|任何|**EINVAL**|未修改|
|未修改|任何|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>备注

**_Get_tzname**函数将检索到的地址的字符字符串表示形式的时区名称或夏时制标准时间区域名称 (DST) *timeZoneName*具体取决于索引值，以及在字符串的大小*pReturnValue*。 如果*timeZoneName*是**NULL**和*sizeInBytes*为零，只需区域，以字节为单位返回在任一时间的字符串的大小*pReturnValue*. 标准时区的索引值必须为 0，夏令时标准时区的索引值必须为 1；索引的任何其他值都具有不确定的结果。

### <a name="index-values"></a>索引值

|*index*|内容*timeZoneName*|*timeZoneName*默认值|
|-------------|--------------------------------|----------------------------------|
|0|时区名称|"PST"|
|1|夏令时标准时区名称|"PDT"|
|> 1 或 < 0|**errno**设置为**EINVAL**|未修改|

除非在运行时显式更改值，默认值分别为 "PST" 和 "PDT"。  这些字符数组的大小受**TZNAME_MAX**值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
