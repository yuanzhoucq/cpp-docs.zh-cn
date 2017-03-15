---
title: "_chdrive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chdrive"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "chdrive"
  - "_chdrive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_chdrive 函数"
  - "chdrive 函数"
  - "驱动器, 更改"
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _chdrive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改当前工作驱动器。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### 参数  
 `drive`  
 整数1到26指定当前的工作驱动器\(1\=A，2\=B，等等\)。  
  
## 返回值  
 零 （0），如果成功更改了当前工作的驱动程序；否则为\-1。  
  
## 备注  
 如果 `drive` 不在范围从 1 到 26，调用参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续， **\_chdrive**函数返回\-1，`errno`设置为`EACCES`，并且 `_doserrno` 设置为 `ERROR_INVALID_DRIVE`  
  
 **\_chdrive** 函数不是线程安全的，因为这取决于 **SetCurrentDirectory** 功能，它本身不是线程安全的。  若要在多线程应用程安全的使用 **\_chdrive** ，则必须提供你自己的线程同步。  有关更多信息，转到[MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542) 搜索 **SetCurrentDirectory**。  
  
 **\_chdrive** 功能只转换当前工作的驱动器；**\_chdir** 更改当前工作目录。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**\_chdrive**|\<direct.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_getdrive](../../c-runtime-library/reference/getdrive.md)中的示例。  
  
## .NET Framework 等效项  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)