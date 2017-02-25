---
title: "_getdcwd_nolock、_wgetdcwd_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wgetdcwd_nolock"
  - "_getdcwd_nolock"
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
apitype: "DLLExport"
f1_keywords: 
  - "_wgetdcwd_nolock"
  - "tgetdcwd_nolock"
  - "wgetdcwd_nolock"
  - "_getdcwd_nolock"
  - "_tgetdcwd_nolock"
  - "getdcwd_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getdcwd_nolock 函数"
  - "_tgetdcwd_nolock 函数"
  - "_wgetdcwd_nolock 函数"
  - "当前工作目录"
  - "[C++], 当前工作"
  - "getdcwd_nolock 函数"
  - "tgetdcwd_nolock 函数"
  - "wgetdcwd_nolock 函数"
  - "工作目录"
ms.assetid: d9bdf712-43f8-4173-8f9a-844e82beaa97
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _getdcwd_nolock、_wgetdcwd_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的驱动器上获取当前工作目录的完整路径。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_getdcwd_nolock(   
   int drive,  
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetdcwd_nolock(   
   int drive,  
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### 参数  
 `drive`  
 磁盘驱动器。  
  
 `buffer`  
 路径的存储位置。  
  
 `maxlen`  
 路径的字符最大长度：`_getdcwd`为`_wgetdcwd`和 `char`为`wchar_t`。  
  
## 返回值  
 请参见 [\_getdcwd、\_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)。  
  
## 备注  
 `_getdcwd_nolock` 和 `_wgetdcwd_nolock` 与 `_getdcwd` 和 `_wgetdcwd`分别是相同的，除了它们不能避免来自由其他线程的干扰。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetdcwd_nolock`|`_getdcwd_nolock`|`_getdcwd_nolock`|`_wgetdcwd_nolock`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getdcwd_nolock`|\<direct.h\>|  
|`_wgetdcwd_nolock`|\<direct.h\> or \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)