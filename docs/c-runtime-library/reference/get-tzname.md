---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: bf63b0ade0adc0a2dfa471bbfbeebc0cb2d04911
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919687"
---
# <a name="_get_tzname"></a>_get_tzname

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
*TimeZoneName*的字符串长度，包括 null 结束符。

*timeZoneName*<br/>
用于表示时区名称或夏令时标准时区名称（DST）的字符串的地址，具体取决于*索引*。

*sizeInBytes*<br/>
*TimeZoneName*字符串的大小（以字节为单位）。

*index*<br/>
要检索的两个时区名称之一的索引。

|*index*|*TimeZoneName*的内容|*timeZoneName*默认值|
|-|-|-|
|0|时区名称|"PST"|
|1|夏令时标准时区名称|"PDT"|
|> 1 或 < 0|**errno**设置为**EINVAL**|未修改|

除非在运行时显式更改值，默认值分别为 "PST" 和 "PDT"。

## <a name="return-value"></a>返回值

如果成功，则为零; 否则为**errno**类型值。

如果*timeZoneName*为**NULL**，或者*sizeInBytes*为零或小于零（但不是两者），则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

### <a name="error-conditions"></a>错误条件

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|返回值|*TimeZoneName*的内容|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|TZ 名称的大小|**Null**|0|0 或 1|0|未修改|
|TZ 名称的大小|any|> 0|0 或 1|0|TZ 名称|
|未修改|**Null**|> 0|any|**EINVAL**|未修改|
|未修改|any|零|any|**EINVAL**|未修改|
|未修改|any|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>备注

**_Get_tzname**函数根据索引值以及*pReturnValue*中字符串的大小，检索当前时区名称或夏令时标准时区名称（DST）的字符串表示形式，以*timeZoneName*地址。 如果*timeZoneName*为**NULL** ，并且*sizeInBytes*为零，则在*pReturnValue*中返回保留指定时区和终止 NULL 的字符串大小（以字节为单位）。 标准时区的索引值必须为0，对于日光标准时区，索引值必须为 1;*index*的任何其他值都具有不确定的结果。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="example"></a>示例

此示例调用 **_get_tzname**以获取所需的缓冲区大小，以显示当前的标准时区名称、分配该大小的缓冲区、再次调用 **_get_tzname**以加载缓冲区中的名称，并将其输出到控制台。

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

|例程|必需的标头|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
