---
title: "全局变量 | Microsoft Docs"
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
  - "c.variables"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "全局变量"
  - "全局变量, Microsoft 运行库"
  - "变量, 全局"
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 全局变量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft C 运行时库提供了以下全局变量或宏。  已弃用几个全局变量或宏，以便使用我们建议的更安全的函数版本，而非全局变量。  
  
|变量|描述|  
|--------|--------|  
|[\_\_argc、\_\_argv、\_\_wargv](../c-runtime-library/argc-argv-wargv.md)|包含命令行参数。|  
|[\_daylight、\_dstbias、\_timezone 和 \_tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|已弃用。  请改为使用 `_get_daylight`、`_get_dstbias`、`_get_timezone` 和 `_get_tzname`。<br /><br /> 调整本地时间；用于一些日期和时间函数。|  
|[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|已弃用。  请改为使用 `_get_errno`、`_set_errno`、`_get_doserrno`、`_set_doserrno`、`perror` 和 `strerror`。<br /><br /> 存储错误代码和相关信息。|  
|[\_environ、\_wenviron](../c-runtime-library/environ-wenviron.md)|已弃用。  请改为使用 `getenv_s`、`_wgetenv_s`、`_dupenv_s`、`_wdupenv_s`、`_putenv_s` 和 `_wputenv_s`。<br /><br /> 指向进程环境字符串的指针数组的指针；在启动时进行初始化。|  
|[\_fmode](../c-runtime-library/fmode.md)|已弃用。  请改为使用 `_get_fmode` 或 `_set_fmode`。<br /><br /> 设置默认文件转换模式。|  
|[\_iob](../c-runtime-library/iob.md)|控制台、文件和设备的 I\/O 控制结构的数组。|  
|[\_pctype、\_pwctype、\_wctype、\_mbctype、\_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|包含由 character\-classification 函数使用的信息。|  
|[\_pgmptr、\_wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|已弃用。  请改为使用 `_get_pgmptr` 或 `_get_wpgmptr`。<br /><br /> 在程序启动时初始化到该程序的完全限定路径或相对路径、完整程序名或不包含其文件扩展名的程序名，具体取决于调用该程序的方式。|  
  
## 请参阅  
 [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)   
 [全局常量](../c-runtime-library/global-constants.md)   
 [\_\_argc、\_\_argv、\_\_wargv](../c-runtime-library/argc-argv-wargv.md)   
 [\_get\_daylight](../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../c-runtime-library/reference/get-tzname.md)   
 [perror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [\_get\_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [\_set\_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [\_get\_errno](../c-runtime-library/reference/get-errno.md)   
 [\_set\_errno](../c-runtime-library/reference/set-errno.md)   
 [\_dupenv\_s、\_wdupenv\_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)   
 [getenv、\_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [\_putenv、\_wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)   
 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md)   
 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)