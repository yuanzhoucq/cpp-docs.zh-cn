---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: b2537a3bbfd2b5cec6bdf149c520aac7e3344b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362187"
---
# <a name="_tzset"></a>_tzset

设置时间环境变量。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
void _tzset( void );
```

## <a name="remarks"></a>备注

**_tzset**函数使用环境变量**TZ**的当前设置将值分配给三个全局变量 **：_daylight、_timezone****_timezone**和 **_tzname**。 这些变量由[_ftime](ftime-ftime32-ftime64.md)和[本地时间](localtime-localtime32-localtime64.md)函数用于从协调的通用时间 （UTC） 到本地时间进行修正，以及根据系统时间计算 UTC[的时间](time-time32-time64.md)函数。 使用以下语法设置**TZ**环境变量：

> **设置 TZ_**_tzn_ \[ **+**&#124;**-**=*hh*\[**：**_mm_\[**：**_ss_= =*dzn*|

|参数|说明|
|-|-|
| *茨恩* | 三个字母时区名称，如 PST。 必须指定从本地时间到 UTC 的正确偏移量。 |
| *hh* | UTC 和本地时间之间的差异（以小时为单位）。 (+) 号对于正值可选。 |
| *毫米* | 分钟。 由冒号 **（）** 与*hh*分离 。 |
| *ss* | 秒。 由冒号 **（）** 与*mm*分隔。 |
| *德兹* | 三字母夏令时区域，如 PDT。 如果夏令时在局部地区从未有效，则设置**TZ**而不为*dzn*的值。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。 |

> [!NOTE]
> 在计算时间差异的符号时一定要小心。 由于时间差异是从本地时间到 UTC 间（不是相反）的偏移量，因此其符号可能会与你直觉上判断的符号相反。 对于早于 UTC 的时区，时间差异为负；对于晚于 UTC 的时区，时间差异为正。

例如，要将**TZ**环境变量设置为对应于德国的当前时区，请在命令行上输入以下内容：

> **设置 TZ=GST-1GDT**

此命令使用 GST 以指示德国标准时间，假定 UTC 晚于德国时间一小时（即德国时间早于 UTC 一小时），并假定德国遵循夏令时制。

如果未设置**TZ**值，**则_tzset**尝试使用操作系统指定的时区信息。 在 Windows 操作系统中，此信息在控制面板的日期/时间应用程序中指定。 如果 **_tzset**无法获得此信息，则默认情况下使用 PST8PDT，这表示太平洋时区。

根据**TZ**环境变量值，当调用 **_tzset**时，将以下值分配给 **_daylight、_timezone**和 **_tzname**的全局变量： **_timezone**

|全局变量|描述|默认值|
|---------------------|-----------------|-------------------|
|**_daylight**|如果在**TZ**设置中指定了夏令时区域，则非零值;否则，0。|1|
|**_timezone**|UTC 和当地时间之间的差异（以秒为单位）。|28800（28800 秒等于 8 小时）|
|**_tzname**[0]|**来自 TZ**环境变量的时区名称的字符串值;如果**TZ**尚未设置，则为空。|PST|
|**_tzname**[1]|夏令时区域的字符串值;如果**从 TZ**环境变量中省略夏令时区域，则为空。|PDT|

上表中显示**的_daylight**和 **_tzname**数组的默认值对应于"PST8PDT"。 如果从**TZ**环境变量中省略 DST 区域，**则_daylight**的值为 0，[并且 _ftime、gmtime](ftime-ftime32-ftime64.md)和[本地时间](localtime-localtime32-localtime64.md)函数返回 0 的 DST 标志。 [gmtime](gmtime-gmtime32-gmtime64.md)

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_tzset**功能特定于 Microsoft。 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>另请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
