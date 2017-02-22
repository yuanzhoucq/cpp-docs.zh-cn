---
title: "timespec_get，_timespec32_get _timespec64_get1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "timespec_get"
  - "_timespec32_get"
  - "_timespec64_get"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "timespec_get"
  - "_timespec32_get"
  - "_timespec64_get"
  - "time/timespec_get"
  - "time/_timespec32_get"
  - "time/_timespec64_get"
  - "timespec"
  - "_timespec32"
  - "_timespec64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "timespec_get 函数"
  - "_timespec32_get 函数"
  - "_timespec64_get 函数"
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# timespec_get、_timespec32_get、_timespec64_get
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基于指定时间基准，将第一个参数指向的间隔设置为当前日历时间。  
  
## 语法  
  
```  
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
  
#### 参数  
 `time_spec`  
 设置为自时期开始以来的时间（以秒和纳秒为单位）的结构的指针。  
  
 `base`  
 一个特定于实现的非零值，指定时间基准。  
  
## 返回值  
 如果成功，则值为 `base`，否则它返回零。  
  
## 备注  
 `timespec_get` 函数设置 `time_spec` 参数指向的结构中的当前时间。 此结构的所有版本都具有两个成员，即 `tv_sec` 和 `tv_nsec`。`tv_sec` 值设置为自 `base` 指定的时期开始以来的整秒数，`tv_nsec` 设置为开始以来的整纳秒数（按系统时钟分辨率进行舍入）。  
  
 **Microsoft 专用**  
  
 这些函数仅支持 `TIME_UTC` 作为 `base` 值。 这会将 `time_spec` 值设置为自时期开始（协调世界时 \(UTC\) 的 1970 年 1 月 1 日午夜）以来的秒数和纳秒数。 在 `struct _timespec32` 中，`tv_sec` 是 `__time32_t` 值。 在 `struct _timespec64` 中，`tv_sec` 是 `__time64_t` 值。 在 `struct timespec` 中，`tv_sec` 是 `time_t` 类型，其长度为 32 位或 64 位，具体取决于是否定义预处理器宏 \_USE\_32BIT\_TIME\_T。`timespec_get` 函数是内联函数，如果定义 \_USE\_32BIT\_TIME\_T，则它调用 `_timespec32_get`；否则它调用 `_timespec64_get`。  
  
 **结束 Microsoft 专用**  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`timespec_get`, `_timespec32_get`, `_timespec64_get`|C: \<time.h\>、C\+\+: \<ctime\> 或 \<time.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_utime、\_utime32、\_utime64、\_wutime、\_wutime32、\_wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)