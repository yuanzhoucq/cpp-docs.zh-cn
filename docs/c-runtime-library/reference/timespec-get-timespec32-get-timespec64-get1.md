---
title: timespec_get，_timespec32_get _timespec64_get1
ms.date: 11/04/2016
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: 1591189ff2db78605c334e72ac3be13876afc81d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155545"
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get、_timespec32_get、_timespec64_get

基于指定时间基准，将第一个参数指向的间隔设置为当前日历时间。

## <a name="syntax"></a>语法

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>参数

*time_spec*<br/>
设置为自时期开始以来的时间（以秒和纳秒为单位）的结构的指针。

*base*<br/>
一个特定于实现的非零值，指定时间基准。

## <a name="return-value"></a>返回值

值*基*如果成功，否则它将返回零。

## <a name="remarks"></a>备注

**Timespec_get**函数将由指向该结构中设置的当前时间*time_spec*参数。 此结构的所有版本都具有两个成员**tv_sec**并**tv_nsec**。 **Tv_sec**值设置为整秒数和**tv_nsec**到整纳秒数，舍入到系统时钟的分辨率所指定的时期开始以来*基*。

**Microsoft 专用**

这些函数仅支持**TIME_UTC**作为*基*值。 这将设置*time_spec*到数秒和纳秒由于时期开始，午夜，自 1970 年 1 月 1 日协调世界时 (UTC) 的值。 在中**struct** **_timespec32**， **tv_sec**是 **__time32_t**值。 在中**struct** **_timespec64**， **tv_sec**是 **__time64_t**值。 在中**struct** **timespec**， **tv_sec**是**time_t**类型，这是 32 位或 64 位的长度，具体取决于预处理器定义宏 _USE_32BIT_TIME_T。 **Timespec_get**函数是内联函数调用 **_timespec32_get**如果定义 _USE_32BIT_TIME_T; 否则它会调用 **_timespec64_get**。

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h>、C++: \<ctime> 或 \<time.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
