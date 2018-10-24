---
title: _get_tzname | Microsoft 文档
ms.custom: ''
ms.date: 10/22/2018
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
ms.openlocfilehash: d773d5d98466963ef621cc3fa7bc5ab8b4acc40a
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990303"
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
字符串长度*timeZoneName*包括 null 终止符。

*timeZoneName*<br/>
具体取决于所在的时区名称或夏令时标准时区名称 (DST) 的表示形式的字符字符串的地址*索引*。

*sizeInBytes*<br/>
大小*timeZoneName*字符以字节为单位的字符串。

*index*<br/>
要检索的两个时区名称之一的索引。

|*index*|内容*timeZoneName*|*timeZoneName*默认值|
|-|-|-|
|0|时区名称|"PST"|
|1|夏令时标准时区名称|"PDT"|
|> 1 或 < 0|**errno**设置为**EINVAL**|未修改|

除非在运行时显式更改值，默认值分别为 "PST" 和 "PDT"。

## <a name="return-value"></a>返回值

如果成功，则为零否则为**errno**键入值。

如果任一*timeZoneName*是**NULL**，或*sizeInBytes*为零或小于零 （但不是两者），无效参数处理程序调用时，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|返回值|内容*timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|TZ 名称的大小|**NULL**|0|0 或 1|0|未修改|
|TZ 名称的大小|任何|> 0|0 或 1|0|TZ 名称|
|未修改|**NULL**|> 0|任何|**EINVAL**|未修改|
|未修改|任何|零|任何|**EINVAL**|未修改|
|未修改|任何|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>备注

**_Get_tzname**函数将检索到的地址的当前时区名称或夏令时标准时区名称 (DST) 的字符字符串表示形式*timeZoneName*具体取决于索引值，以及在字符串的大小*pReturnValue*。 如果*timeZoneName*是**NULL**并*sizeInBytes*是零，以保存指定的时区字符串的大小和终止 null 以字节为单位返回中*pReturnValue*。 索引值必须是标准时区的时间为 0 或 1 表示夏令时标准时区的时间;任何其他值*索引*具有不确定的结果。

## <a name="example"></a>示例

此示例会调用 **_get_tzname**若要获得所需的缓冲区大小，以显示当前夏令时标准时区名称，将分配一个缓冲区的大小，调用 **_get_tzname**再次以加载中的名称缓冲，并将其打印到控制台。

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>输出

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
