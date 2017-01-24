---
title: "标准类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__time64_t"
  - "_diskfree_t"
  - "_CRT_DUMP_CLIENT"
  - "_fsize_t"
  - "__timeb64"
  - "File"
  - "__utimeb64"
  - "jmp_buf"
  - "__finddata64_t"
  - "_wfinddata_t"
  - "_finddata_t"
  - "utimbuf64"
  - "wint_t"
  - "wctrans_t"
  - "wctype_t"
  - "_HFILE"
  - "_secerr_handler_func"
  - "clock_t"
  - "fpos_t"
  - "_dev_t"
  - "time64_t"
  - "wfinddata64_t"
  - "stat64"
  - "ldiv_t"
  - "_EXCEPTION_POINTERS"
  - "terminate_function"
  - "size_t"
  - "timeb64"
  - "tm"
  - "_HEAPINFO"
  - "unexpected_function"
  - "_CrtMemState"
  - "_se_translator_function"
  - "sig_atomic_t"
  - "_CRT_REPORT_HOOK"
  - "_complex"
  - "_w_finddatai64_t"
  - "_timeb"
  - "_onexit_t"
  - "_RTC_ErrorNumber"
  - "lconv"
  - "_PNH"
  - "_off_t"
  - "ptrdiff_t"
  - "time_t"
  - "_FPIEEE_RECORD"
  - "_exception"
  - "__w_finddata64_t"
  - "__stat64"
  - "_utimbuf"
  - "__utimbuf64"
  - "div_t"
  - "_CRT_ALLOC_HOOK"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__finddata64_t 类型"
  - "__stat64 类型"
  - "__time64_t 类型"
  - "__timeb64 类型"
  - "__utimbuf64 类型"
  - "__wfinddata64_t 类型"
  - "_complex 类型"
  - "_CRT_ALLOC_HOOK 类型"
  - "_CRT_DUMP_CLIENT 类型"
  - "_CRT_REPORT_HOOK 类型"
  - "_dev_t 类型"
  - "_diskfree_t 类型"
  - "_exception 类型"
  - "_EXCEPTION_POINTERS 类型"
  - "_finddata_t 类型"
  - "_FPIEEE_RECORD 类型"
  - "_fsize_t 类型"
  - "_HEAPINFO 类型"
  - "_HFILE 类型"
  - "_locale_t 类型"
  - "_off_t 类型"
  - "_onexit_t 类型"
  - "_PNH 类型"
  - "_RTC_ErrorNumber 类型"
  - "_se_translater_function 类型"
  - "_secerr_handler_func 类型"
  - "_stat 类型"
  - "_timeb 类型"
  - "_utimbuf 类型"
  - "_wfinddata_t 类型"
  - "_wfinddatai64_t 类型"
  - "clock_t 类型"
  - "复杂类型"
  - "CRT, 标准类型"
  - "CRT_ALLOC_HOOK 类型"
  - "CRT_DUMP_CLIENT 类型"
  - "CRT_REPORT_HOOK 类型"
  - "CrtMemState 类型"
  - "dev_t 类型"
  - "diskfree_t 类型"
  - "div_t 类型"
  - "exception 类型"
  - "EXCEPTION_POINTERS 类型"
  - "FILE 常量"
  - "finddata_t 类型"
  - "FPIEEE_RECORD 类型"
  - "fpos_t 类型"
  - "HEAPINFO 类型"
  - "HFILE 类型"
  - "intptr_t 类型"
  - "jmp_buf 类型"
  - "lconv 类型"
  - "ldiv_t 类型"
  - "off_t 类型"
  - "onexit_t 类型"
  - "PNH 类型"
  - "ptrdiff_t 类型"
  - "RTC_ErrorNumber 类型"
  - "se_translater_function 类型"
  - "secerr_handler_func 类型"
  - "sig_atomic_t 类型"
  - "size_t 类型"
  - "stat 类型"
  - "terminate_function 类型"
  - "time_t 类型"
  - "timeb 类型"
  - "timeb64"
  - "tm 类型"
  - "uintptr_t 类型"
  - "unexpected_function typedef"
  - "utimbuf 类型"
  - "va_list 类型"
  - "wchar_t 类型"
  - "wctrans_t 类型"
  - "wctype_t 类型"
  - "wfinddata_t 类型"
  - "wfinddatai64_t 类型"
  - "wint_t 类型"
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 标准类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 运行库定义下列标准类型和 typedef。  
  
### 定宽整型类型 \(stdint.h\)  
  
|名称|等效内置类型|  
|--------|------------|  
|int8\_t、uint8\_t|signed char、unsigned char|  
|int16\_t、int16\_t|short、unsigned short|  
|int32\_t、uint32\_t|int、unsigned int|  
|int64\_t、int64\_t|long long、unsigned long long|  
|int\_least8\_t、uint\_least8\_t|signed char、unsigned char|  
|int\_least16\_t、uint\_least16\_t|short、unsigned short|  
|int\_least32\_t、uint\_least32\_t|int、unsigned int|  
|int\_least64\_t、uint\_least64\_t|long long、unsigned long long|  
|int\_fast8\_t、uint\_fast8\_t|signed char、unsigned char|  
|int\_fast16\_t、uint\_fast16\_t|int、unsigned int|  
|int\_fast32\_t、uint\_fast32\_t|int、unsigned int|  
|int\_fast64\_t、uint\_fast64\_t|long long、unsigned long long|  
|intmax\_t、uintmax\_t|long long、unsigned long long|  
  
|类型|描述|声明位置|  
|--------|--------|----------|  
|`clock_t` \(long\)|存储时间值；由 [clock](../c-runtime-library/reference/clock.md) 使用。|TIME.H|  
|`_complex` 结构|存储复数的实数部分和虚数部分；由 [\_cabs](../c-runtime-library/reference/cabs.md) 使用。|MATH.H|  
|`_CRT_ALLOC_HOOK`|用户定义的挂钩函数的类型定义。  在 [\_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md) 中使用。|CRTDBG.H|  
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|将在 [\_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md) 中调用的回调函数的类型定义。|CRTDBG.H|  
|`_CrtMemState` 结构|提供有关 C 运行时调试堆的当前状态的信息。|CRTDBG.H|  
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|将在 [\_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 中调用的回调函数的类型定义。<br /><br /> 此函数的参数包括：报告类型、输出消息和回调函数的返回值。|CRTDBG.H|  
|`dev_t`、`_dev_t` short 或 unsigned integer|表示设备句柄。|SYS\\TYPES.H|  
|`_diskfree_t`  结构|包含有关磁盘驱动器的信息。  由 [\_getdiskfree](../c-runtime-library/reference/getdiskfree.md) 使用。|DOS.H 和 DIRECT.H|  
|`div_t`、`ldiv_t` 和 `lldiv_t` 结构|存储 [div](../c-runtime-library/reference/div.md)、[ldiv](../c-runtime-library/reference/ldiv-lldiv.md) 和 [lldiv](../c-runtime-library/reference/ldiv-lldiv.md) 分别返回的值。|STDLIB.H|  
|`errno_t` integer|用于处理 `errno` 的错误代码的函数返回类型或参数。|STDDEF.H、<br /><br /> CRTDEFS.H|  
|`_exception` 结构|存储 [\_matherr](../c-runtime-library/reference/matherr.md) 的错误信息。|MATH.H|  
|`_EXCEPTION_POINTERS`|包含一个异常记录。  有关详细信息，请参阅 [EXCEPTION\_POINTERS](http://msdn.microsoft.com/library/windows/desktop/ms679331)。|FPIEEE.H|  
|`FILE`  结构|存储有关流的当前状态的信息；在所有流 I\/O 操作中使用。|STDIO.H|  
|`_finddata_t`、`_wfinddata_t`、`_finddata32_t`、`_wfinddata32_t`、`_finddatai64_t`、`_wfinddatai64_t`、`__finddata64_t`、`__wfinddata64_t`、`__finddata32i64_t`、`__wfinddata32i64_t`、`__finddata64i32_t`、`__wfinddata64i32_t` 结构|存储 [\_findfirst、\_wfindfirst 和相关的函数](../c-runtime-library/reference/findfirst-functions.md) 和 [\_findnext、\_wfindnext 和相关函数](../c-runtime-library/reference/findnext-functions.md) 返回的文件属性信息。  有关结构成员的信息，请参阅 [文件名搜索函数](../c-runtime-library/filename-search-functions.md)。|IO.H、WCHAR.H|  
|`_FPIEEE_RECORD`  结构|包含有关 IEEE 浮点异常的信息；由 [\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md) 传递给用户定义的陷阱处理程序。|FPIEEE.H|  
|`fpos_t`（long integer、`__int64` 或结构，取决于目标平台）|由 [fgetpos](../c-runtime-library/reference/fgetpos.md) 和 [fsetpos](../c-runtime-library/reference/fsetpos.md) 用于记录信息以在文件中唯一指定每个位置。|STDIO.H|  
|`_fsize_t` \(unsigned long integer\)|用于表示文件的大小。|IO.H、<br /><br /> WCHAR.H|  
|`_HEAPINFO` 结构|包含有关 [\_heapwalk](../c-runtime-library/reference/heapwalk.md) 的下一个堆条目的信息。|MALLOC.H|  
|`_HFILE` \(void \*\)|操作系统文件句柄。|CRTDBG.H|  
|`imaxdiv_t`|[imaxdiv](../c-runtime-library/reference/imaxdiv.md) 函数返回的值的类型，包含商和余数。|inttypes.h|  
|`ino_t`、`_ino_t` \(unsigned short\)|用于返回状态信息。|WCHAR.H|  
|`intmax_t`|一个带符号整数类型，能够表示任何带符号整数类型的任何值。|stdint.h|  
|`intptr_t`（long integer 或 `__int64`，取决于目标平台）|在 Win32 和 Win64 平台上存储指针（或 HANDLE）。|STDDEF.H 和其他包含文件|  
|`jmp_buf` 数组|由 [setjmp](../c-runtime-library/reference/setjmp.md) 和 [longjmp](../c-runtime-library/reference/longjmp.md) 用于保存和还原程序环境。|SETJMP.H|  
|`lconv` 结构|包含数字值在不同国家\/地区的格式设置规则。  由 [localeconv](../c-runtime-library/reference/localeconv.md) 使用。|LOCALE.H|  
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12`（long double 或 unsigned char 数组）|用于表示一个长双精度值。|STDLIB.H|  
|`_locale_t` 结构|存储当前区域设置值；在所有区域设置特定 C 运行库中使用。|CRTDEF.H|  
|`mbstate_t`|跟踪多字节字符转换的状态。|WCHAR.H|  
|`off_t`、`_off_t` long integer|表示文件偏移量值。|WCHAR.H、SYS\\TYPES.H|  
|`_onexit_t`,<br /><br /> `_onexit_m_t` 指针|由 [\_onexit、\_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md) 返回。|STDLIB.H|  
|指向函数的 `_PNH` 指针|[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) 的参数的类型。|NEW.H|  
|`ptrdiff_t`（long integer 或 `__int64`，取决于目标平台）|两个指针相减的结果。|CRTDEFS.H|  
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|调用纯虚函数时调用的回调函数的类型定义。  由 [\_get\_purecall\_handler \_set\_purecall\_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 使用。  `_purecall_handler` 函数应具有 void 返回类型。|STDLIB.H|  
|`_RTC_error_fn` 类型定义|将处理运行时错误检查的函数的类型定义。  在 [\_RTC\_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md) 中使用。|RTCAPI.H|  
|`_RTC_error_fnW` 类型定义|将处理运行时错误检查的函数的类型定义。  在 [\_RTC\_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md) 中使用。|RTCAPI.H|  
|`_RTC_ErrorNumber` 枚举|定义 [\_RTC\_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) 和 [\_RTC\_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md) 的错误条件。|RTCAPI.H|  
|`_se_translator_function`|转换异常的回调函数的类型定义。  第一个参数是异常代码，第二个参数是异常记录。  由 [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md) 使用。|EH.H|  
|`sig_atomic_t` integer|可修改为原子实体（即使在出现异步中断时也是如此）的对象的类型；与 [signal](../c-runtime-library/reference/signal.md) 一起使用。|SIGNAL.H|  
|`size_t`（unsigned \_\_int64 或 unsigned integer，取决于目标平台）|`sizeof` 运算符的结果。|CRTDEFS.H 和其他包含文件|  
|`_stat` 结构|包含 [\_stat](../c-runtime-library/reference/stat-functions.md) 和 [\_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 返回的文件状态信息。|SYS\\STAT.H|  
|`__stat64` 结构|包含 [\_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[\_stat64](../c-runtime-library/reference/stat-functions.md) 和 [\_wstat64](../c-runtime-library/reference/stat-functions.md) 返回的文件状态信息。|SYS\\STAT.H|  
|`_stati64` 结构|包含 [\_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[\_stati64](../c-runtime-library/reference/stat-functions.md) 和 [\_wstati64](../c-runtime-library/reference/stat-functions.md) 返回的文件状态信息。|SYS\\STAT.H|  
|`terminate_function` 类型定义|调用 [terminate](../c-runtime-library/reference/terminate-crt.md) 时调用的回调函数的类型定义。  由 [set\_terminate](../c-runtime-library/reference/set-terminate-crt.md) 使用。|EH.H|  
|`time_t`（\_\_int64 或 long integer）|在 [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[time](../c-runtime-library/reference/time-time32-time64.md)、[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 和 [gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 中表示时间值。  自 1970 年 1 月 1 日 0:00 \(UTC\) 时起的秒数。  如果定义 \_USE\_32BIT\_TIME\_T，则 `time_t` 为 long integer。  如果未定义，则它为 64 位整数。|TIME.H、<br /><br /> SYS\\STAT.H、<br /><br /> SYS\\TIMEB.H|  
|`__time32_t` \(long integer\)|在 [mktime、\_mktime32、\_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 和 [localtime、\_localtime32、\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) 中表示时间值。|CRTDEFS.H、SYS\\STAT.H、<br /><br /> SYS\\TIMEB.H|  
|`__time64_t` \(`__int64`\)|在 [mktime、\_mktime32、\_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[\_ctime64、\_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) 和 [\_time64](../c-runtime-library/reference/time-time32-time64.md) 中表示时间值。|TIME.H、<br /><br /> SYS\\STAT.H、<br /><br /> SYS\\TIMEB.H|  
|`_timeb` 结构|由 [\_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 用于存储当前系统时间。|SYS\\TIMEB.H|  
|`__timeb32` 结构|由 [\_ftime, \_ftime32, \_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 用于存储当前系统时间。|SYS\\TIMEB.H|  
|`__timeb64` 结构|由 [\_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 用于存储当前系统时间。|SYS\\TIMEB.H|  
|`tm` 结构|由 [asctime、\_wasctime](../c-runtime-library/reference/asctime-wasctime.md)、[asctime\_s、\_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)、[gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)、[localtime、\_localtime32、\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[localtime\_s, \_localtime32\_s, \_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)、[mktime、\_mktime32、\_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) 和 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 用于存储和检索时间信息。|TIME.H|  
|`uintmax_t`|一个带符号整数类型，能够表示任何带符号整数类型的任何值。|stdint.h|  
|`uintptr_t`（long integer 或 `__int64`，取决于目标平台）|`intptr_t` 的 unsigned integer 或 unsigned \_\_int64 版本|STDDEF.H 和其他包含文件|  
|`unexpected_function`|调用 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 时调用的回调函数的类型定义。  由 [set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md) 使用。|EH.H|  
|`_utimbuf` 结构|存储 [\_utime、\_wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [\_futime、\_futime32、\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 用于更改文件修改日期的文件访问时间和修改时间。|SYS\\UTIME.H|  
|`_utimbuf32` 结构|存储 [\_utime、\_utime32、\_utime64、\_wutime、\_wutime32、\_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [\_futime、\_futime32、\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 用于更改文件修改日期的文件访问时间和修改时间。|SYS\\UTIME.H|  
|`__utimbuf64` 结构|由 [\_utime64, \_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 用于存储当前时间。|SYS\\UTIME.H|  
|`va_list` 结构|用于保留 [va\_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 和 [va\_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 宏所需的信息。  被调用的函数将可作为参数传递的 `va_list` 类型的变量声明为另一个函数。|STDARG.H、<br /><br /> CRTDEFS.H|  
|`wchar_t` 宽字符|用于为国际市场编写可移植程序。|STDDEF.H、STDLIB.H、<br /><br /> CRTDEFS.H、<br /><br /> SYS\\STAT.H|  
|`wctrans_t` integer|表示区域设置特定字符映射。|WCTYPE.H|  
|`wctype_t` integer|可表示任何语言字符集的所有字符。|WCHAR.H、<br /><br /> CRTDEFS.H|  
|`wint_t` integer|可保留任何宽字符或宽文件尾值的数据对象的类型。|WCHAR.H、<br /><br /> CRTDEFS.H|  
  
## 请参阅  
 [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)