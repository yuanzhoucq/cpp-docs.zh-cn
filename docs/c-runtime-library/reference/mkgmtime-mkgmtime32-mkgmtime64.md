---
title: "_mkgmtime、_mkgmtime32、_mkgmtime64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mkgmtime32"
  - "_mkgmtime64"
  - "_mkgmtime"
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
  - "_mkgmtime64"
  - "mkgmtime32"
  - "_mkgmtime32"
  - "mkgmtime"
  - "mkgmtime64"
  - "_mkgmtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mkgmtime32 函数"
  - "时间函数"
  - "mkgmtime 函数"
  - "_mkgmtime 函数"
  - "转换时间"
  - "mkgmtime64 函数"
  - "_mkgmtime64 函数"
  - "_mkgmtime32 函数"
  - "时间, 转换"
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mkgmtime、_mkgmtime32、_mkgmtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将由表示 UTC 时间转换为 `tm``struct` 为 UTC 时间表示 `time_t` 类型。  
  
## 语法  
  
```  
  
time_t _mkgmtime(  
   struct tm*   
timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm*   
timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm*   
timeptr  
);  
  
```  
  
#### 参数  
 `timeptr`  
 调整为 UTC 时间作为指针 `struct``tm` 将转换。  
  
## 返回值  
 类型的数量 `__time32_t` 或 `__time64_t` 自 1970 年 1 月 1 日，以协调世界时 \(UTC\) 午夜以来经过的表示的秒数。 如果该日期超出范围 （请参见备注部分） 或输入不能解释为一个有效的时间，则返回值为 – 1。  
  
## 备注  
 `_mkgmtime32` 和 `_mkgmtime64` 函数将转换为 UTC 时间 `__time32_t` 或 `__time64_t` 类型表示的 UTC 时间。 若要将本地时间转换为 UTC 时间，使用 `mktime`, ，`_mktime32`, ，和 `_mktime64` 相反。  
  
 `_mkgmtime` 是一个内联函数，计算结果为 `_mkgmtime64`, ，和 `time_t` 等同于 `__time64_t`。 如果您需要强制编译器将解释 `time_t`为旧的 32 位 `time_t`, ，您可以定义 `_USE_32BIT_TIME_T`。 因为后 2038 年 1 月 18 日，您的应用程序可能失败，所以不推荐 \(32 位的最大范围 `time_t`\)，并且不允许在所有 64 位平台上。  
  
 结构中传递的时间将更改，如下所示，在相同的方式与发生更改时 `_mktime` 函数︰ `tm_wday` 和 `tm_yday` 字段设置为新值的值为基础 `tm_mday` 和 `tm_year`。 指定 `tm` 结构时间时，将 `tm_isdst` 字段设置为：  
  
-   零 \(0\)，指示标准时间有效。  
  
-   大于 0 的值，指示夏令时有效。  
  
-   小于零的值，使用 C 运行时库代码计算有效的是标准时间还是夏令时。  
  
 C 运行库使用 TZ 环境变量来确定正确夏时制时间。 如果未设置 TZ，操作系统将查询以获取正确的区域夏令时时行为。`tm_isdst` 是必填字段。 如果未设置，其值是不确定的返回值和 `mktime` 是不可预知的。  
  
 范围 `_mkgmtime32` 函数为从 1970 年 1 月 1 日午夜到 23:59:59 2038 年 1 月 18 日，UTC 的 UTC。 范围 `_mkgmtime64` 为从 1970 年 1 月 1 日午夜 UTC 到 23:59:59，3000 年 12 月 31 日，UTC。 超出范围日期会导致返回值 – 1。 范围 `_mkgmtime` 取决于是否 `_USE_32BIT_TIME_T` 定义。 如果未定义 （默认值） 范围是 `_mkgmtime64`; 否则为为范围仅限于 32 位各种 `_mkgmtime32`。  
  
 请注意， `gmtime` 和 `localtime` 使用用于转换的单个静态分配的缓冲区。 如果提供此缓冲区 `mkgmtime`, ，以前的内容会被销毁。  
  
## 示例  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## 示例输出  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 下面的示例演示不完整的结构与一周中的天和年的某一天的计算值的填满。  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## 输出  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)