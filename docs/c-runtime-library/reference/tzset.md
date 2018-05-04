---
title: _tzset | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _tzset
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
- _tzset
dev_langs:
- C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15464ac8be075d44a9a42223964239538508a683
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="tzset"></a>_tzset

设置时间环境变量。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
void _tzset( void );
```

## <a name="remarks"></a>备注

**_Tzset**函数使用环境变量的当前设置**TZ**将值分配到三个全局变量： **_daylight**， **_timezone**，和 **_tzname**。 通过使用这些变量[_ftime](ftime-ftime32-ftime64.md)和[localtime](localtime-localtime32-localtime64.md)函数本地时间，并且，通过从协调世界时 (UTC) 进行更正[时间](time-time32-time64.md)函数从系统时间计算 UTC。 使用以下语法设置**TZ**环境变量：

> **设置 TZ =**_tzn_ \[ **+** &#124; **-**]*hh* \[ **:**_mm_\[**:**_ss_]] [*dzn*]

|参数|描述|
|-|-|
*tzn*|三个字母时区名称，如 PST。 必须指定从本地时间到 UTC 的正确偏移量。
*hh*|UTC 和本地时间之间的差异（以小时为单位）。 (+) 号对于正值可选。
*mm*|分钟。 分开*hh*用冒号 (**:**)。
*ss*|秒。 分开*mm*用冒号 (**:**)。
*dzn*|三字母夏令时区域，如 PDT。 如果夏令时永远不会有效在区域中，设置**TZ**没有值*dzn*。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。

> [!NOTE]
> 在计算时间差异的符号时一定要小心。 由于时间差异是从本地时间到 UTC 间（不是相反）的偏移量，因此其符号可能会与你直觉上判断的符号相反。 对于早于 UTC 的时区，时间差异为负；对于晚于 UTC 的时区，时间差异为正。

例如，若要设置**TZ**环境变量以对应于德国，当前所在的时区输入以下命令行上：

> **设置 TZ = GST 1GDT**

此命令使用 GST 以指示德国标准时间，假定 UTC 晚于德国时间一小时（即德国时间早于 UTC 一小时），并假定德国遵循夏令时制。

如果**TZ**未设置值， **_tzset**尝试使用由操作系统指定的时区信息。 在 Windows 操作系统中，此信息在控制面板的日期/时间应用程序中指定。 如果 **_tzset**无法获取此信息，它使用默认值，该值表示太平洋时区的 PST8PDT。

基于**TZ**环境变量值，将以下值分配给全局变量 **_daylight**， **_timezone**，和 **_tzname**时 **_tzset**调用：

|全局变量|描述|默认值|
|---------------------|-----------------|-------------------|
|**_daylight**|如果夏令时的时区中指定的非零值**TZ**设置; 否则为 0。|1|
|**_timezone**|UTC 和当地时间之间的差异（以秒为单位）。|28800（28800 秒等于 8 小时）|
|**_tzname**[0]|从时区名称的字符串值**TZ**环境变量，例如： 空如果**TZ**尚未设置。|PST|
|**_tzname**[1]|夏令时的时区; 的字符串值如果夏令时的时区省略从空**TZ**环境变量。|PDT|

显示有关前面的表中的默认值 **_daylight**和 **_tzname**数组对应于"PST8PDT。 如果 DST 区域省略从**TZ**环境变量、 的值 **_daylight**为 0 和[_ftime](ftime-ftime32-ftime64.md)， [gmtime](gmtime-gmtime32-gmtime64.md)，和[localtime](localtime-localtime32-localtime64.md)函数返回对其 DST 标志的 0。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_Tzset**特定于 Microsoft 的技术支持部门。 有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
