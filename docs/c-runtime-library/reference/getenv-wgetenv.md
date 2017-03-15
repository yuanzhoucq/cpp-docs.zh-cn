---
title: "getenv、_wgetenv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "getenv"
  - "_wgetenv"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wgetenv"
  - "getenv"
  - "_tgetenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tgetenv 函数"
  - "_wgetenv 函数"
  - "环境值"
  - "环境变量"
  - "getenv 函数"
  - "tgetenv 函数"
  - "wgetenv 函数"
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# getenv、_wgetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从当前环境获取值。  有关这些函数的更多安全版本，请参见 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### 参数  
 `varname`  
 环境变量名  
  
## 返回值  
 返回指向包含 `varname`环境表项的指针。  使用返回的指针修改环境变量的值是不安全的。  使用 `_putenv`函数修改环境变量的值。  如果 `varname` 在环境表中未找到，返回值是 `NULL`。  
  
## 备注  
 `getenv` 函数搜索环境变量列表 `varname`。  `getenv` 在Windows操作系统下不区分大小写。  `getenv` 和 `_putenv` 使用环境的副本用全局变量指向该 `_environ` 访问该环境。  `getenv` 仅对数据结构可以访问运行库和不在环境“进程”创建的段由操作系统。  因此，使用 `envp` 参数。[main](../../cpp/main-program-startup.md) 或 [wmain](../../cpp/main-program-startup.md) 的程序可以检索无效信息。  
  
 如果 `varname` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `NULL`。  
  
 `_wsetlocale_wgetenv`  是 `getenv`  的宽字符版本，`_wgetenv` 参数和 的返回值都是宽字符字符串。  `_wenviron` 全局变量是 `_environ`的宽字符版本。  
  
 在 MBCS 程序 \(例如，在 SBCS ASCII 程序\)，`_wenviron` 最初是 `NULL`，因为环境由多字节字符字符串组成。  然后，首次调用 `_wputenv` 或在 MBCS 环境已存在的情况下首次调用 `_wgetenv` 时，将创建相应的宽字符字符串环境。并由`_wenviron`指向。  
  
 同样在 Unicode \(`_wmain`\) 程序，`_environ` 最初是 `NULL`，因为环境由宽字符字符串组成。  然后，首次调用`_putenv`，或者首次调用`getenv`如果一个 \(Unicode\) 环境已经存在，一个对应的环境被创建然后由`_environ`指向。  
  
 当环境的两个副本 \(MBCS 和 Unicode\) 时同时存在于程序，运行时系统必须保留两个副本，导致较慢的执行时间。  例如，只要调用 `_putenv`，对 `_wputenv` 的调用也会自动执行，因此，两个环境字符串对应。  
  
> [!CAUTION]
>  在极少数情况下，当该运行时系统维护一个 Unicode 版本和该环境中的某个多字节版本，这两个环境版本可能无法正确对应。  这是因为，任何单个多字节字符字符串映射到单个 Unicode 字符串，从单个 Unicode 字符串到多字节字符字符串不一定是唯一的。  有关详细信息，请参阅 [\_environ，\_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 函数系列不是线程安全的。  `_getenv` 可以返回字符串指针，当 `_putenv` 修改该字符串时，会导致随机崩溃。  确保对这些函数的调用同步。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 检查或更改 `TZ` 环境变量的值，使用 `getenv`, `_putenv` 和 `_tzset` 是必须的。  有关以下内容的详细信息 `TZ`，	请参见[\_tzset](../../c-runtime-library/reference/tzset.md) and [\_daylight, timezone, and \_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`getenv`|\<stdlib.h\>|  
|`_wgetenv`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getenv.c  
// compile with: /W3  
// This program uses getenv to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *libvar;  
  
   // Get the value of the LIB environment variable.  
   libvar = getenv( "LIB" ); // C4996  
   // Note: getenv is deprecated; consider using getenv_s instead  
  
   if( libvar != NULL )  
      printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects the environment  
   // variable of the current process. The command processor's  
   // environment is not changed.  
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996  
   // Note: _putenv is deprecated; consider using putenv_s instead  
  
   // Get new value.  
   libvar = getenv( "LIB" ); // C4996  
  
   if( libvar != NULL )  
      printf( "New LIB variable is: %s\n", libvar );  
}  
```  
  
  **原始 LIB 变量为：C:\\progra ~1\\devstu~1\\VC\\lib**  
**新的 LIB 变量为：c:\\mylib; c:\\yourlib**   
## .NET Framework 等效项  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_putenv、\_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [环境常量](../../c-runtime-library/environmental-constants.md)