---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c0517c974bf58d502133ccd9868149bd178790d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957620"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get、_timespec32_get、_timespec64_get

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

如果成功，则为*base*的值; 否则返回零。

## <a name="remarks"></a>备注

**Timespec_get**函数设置由*time_spec*参数指向的结构中的当前时间。 此结构的所有版本都具有两个成员，即**tv_sec**和**tv_nsec**。 **Tv_sec**值设置为**tv_nsec**的整数，整秒数和秒数（舍入到系统时钟的分辨率），因为*基数*指定的 epoch 开始。

**Microsoft 专用**

这些函数仅支持**TIME_UTC**作为*基值*。 这会将*time_spec*值设置为自1970年1月1日午夜（1970，协调世界时（UTC）午夜）以来的秒数和纳秒数。 在**struct** **_timespec32**中， **tv_sec**是一个 **__time32_t**值。 在**struct** **_timespec64**中， **tv_sec**是一个 **__time64_t**值。 在**struct** **timespec**中， **tv_sec**是一种**time_t**类型，其长度为32位或64位，具体取决于是否定义了预处理器宏 _USE_32BIT_TIME_T。 **Timespec_get**函数是一个内联函数，如果定义 _USE_32BIT_TIME_T，则调用 **_timespec32_get** ;否则，它会调用 **_timespec64_get**。

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**timespec_get**、 **_timespec32_get**、 **_timespec64_get**|C: \<time.h>、C++: \<ctime> 或 \<time.h>|

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
