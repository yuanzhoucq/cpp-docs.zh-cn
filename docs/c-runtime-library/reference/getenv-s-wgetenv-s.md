---
title: "getenv_s、_wgetenv_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "getenv_s"
  - "_wgetenv_s"
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
  - "getenv_s"
  - "_tgetenv_s"
  - "_wgetenv_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tgetenv_s 函数"
  - "_wgetenv_s 函数"
  - "环境变量"
  - "getenv_s 函数"
  - "tgetenv_s 函数"
  - "wgetenv_s 函数"
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
caps.latest.revision: 42
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getenv_s、_wgetenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从当前环境中获取值。  如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些版本的 [getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md) 具有安全增强功能。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char* buffer,  
   size_t numberOfElements,  
   const char *varname   
);  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *varname   
);  
template <size_t size>  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char (&buffer)[size],  
   const char *varname   
); // C++ only  
template <size_t size>  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t (&buffer)[size],  
   const wchar_t *varname   
); // C++ only  
```  
  
#### 参数  
 `pReturnValue`  
 所需的缓冲区大小，如果找不到该变量，则为 0。  
  
 `buffer`  
 用于存储环境变量值的缓冲区。  
  
 `numberOfElements`  
 `buffer` 的大小。  
  
 `varname`  
 环境变量名称。  
  
## 返回值  
 如果成功，则为零；如果失败，则返回错误代码。  
  
### 错误条件  
  
|`pReturnValue`|`buffer`|`numberOfElements`|`varname`|返回值|  
|--------------------|--------------|------------------------|---------------|---------|  
|`NULL`|任何|any|任何|`EINVAL`|  
|任何|`NULL`|\>0|任何|`EINVAL`|  
|任何|any|任何|`NULL`|`EINVAL`|  
  
 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述，这些错误条件调用无效的参数处理程序。  如果允许执行继续，则这些函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 此外，如果缓冲区太小，这些函数将返回 `ERANGE`。  它们不会调用无效的参数处理程序。  它们将在 `pReturnValue` 中写出所需的缓冲区大小，从而使程序能够使用较大的缓冲区再次调用函数。  
  
## 备注  
 `getenv_s` 函数将搜索 `varname` 的环境变量列表。  在 Windows 操作系统中，`getenv_s` 不区分大小写。  `getenv_s` 和 `_putenv_s` 使用全局变量 `_environ` 所指向环境的副本来访问该环境。  `getenv_s` 只能在可访问运行时库的数据结构上执行，不能在由操作系统对进程创建的环境“段”上执行。  因此，对 [main](../../cpp/main-program-startup.md) 或 [wmain](../../cpp/main-program-startup.md) 使用 `envp` 参数的程序可能会检索无效信息。  
  
 `_wgetenv_s` 是 `getenv_s` 的宽字符版本；`_wgetenv_s` 的参数和返回值都是宽字符字符串。  `_wenviron` 全局变量是 `_environ` 的宽字符版本。  
  
 在 MBCS 程序中（例如，在 SBCS ASCII 程序中），`_wenviron` 最初为 `NULL`，因为环境是由多字节字符字符串组成的。  然后，在首次调用 `_wputenv` 或首次调用 `_wgetenv_s` 时，如果 \(MBCS\) 环境已存在，则将由 `_wenviron` 创建对应的宽字符字符串环境并指向该环境。  
  
 同样，在 Unicode `(_wmain`\) 程序中，`_environ` 最初为 `NULL`，因为环境是由宽字符字符串组成的。  然后，在首次调用 `_putenv` 或在首次调用 `getenv_s` 时，如果 \(Unicode\) 环境已存在，则将由 `_environ` 创建对应的 MBCS 环境并指向该环境。  
  
 当程序中同时存在环境的两个副本（MBCS 和 Unicode）时，运行时系统必须保留这两个副本，而这将减慢执行时间。  例如，当调用 `_putenv` 时，也会自动调用 `_wputenv`，以便两个环境字符串相对应。  
  
> [!CAUTION]
>  在极少数情况下，当运行时系统同时保留环境的 Unicode 版本和多字节版本时，两个环境版本可能不完全对应。  这是因为，虽然任何唯一的多字节字符字符串将映射到唯一的 Unicode 字符串，但从唯一的 Unicode 字符串到多字节字符字符串的映射却不一定是唯一的。  有关详细信息，请参阅 [\_environ、\_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv_s` 和 `_getenv_s` 系列的函数不是线程安全函数。  当 `_putenv_s` 修改字符串时，`_getenv_s` 会返回字符串指针，从而导致随机失败。  确保对这些函数的调用同步。  
  
 在 C\+\+ 中，这些函数的使用由模板重载简化；重载可以自动推导出缓冲区长度，从而不再需要指定大小参数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetenv_s`|`getenv_s`|`getenv_s`|`_wgetenv_s`|  
  
 若要检查或更改 `TZ` 环境变量的值，请按需使用 `getenv_s`、`_putenv` 和 `_tzset`。  有关 `TZ` 的详细信息，请参阅 [\_tzset](../../c-runtime-library/reference/tzset.md) 和 [\_daylight、\_dstbias、\_timezone 和 \_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`getenv_s`|\<stdlib.h\>|  
|`_wgetenv_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_getenv_s.c  
// This program uses getenv_s to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* libvar;  
   size_t requiredSize;  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
   if (requiredSize == 0)  
   {  
      printf("LIB doesn't exist!\n");  
      exit(1);  
   }  
  
   libvar = (char*) malloc(requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the value of the LIB environment variable.  
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects  
   // the environment variable of the current process. The command  
   // processor's environment is not changed.  
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
  
   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the new value of the LIB environment variable.   
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "New LIB variable is: %s\n", libvar );  
  
   free(libvar);  
}  
```  
  
  **原始 LIB 变量是：c:\\vctools\\lib;c:\\vctools\\atlmfc\\lib;c:\\vctools\\PlatformSDK\\lib;c:\\vctools\\Visual Studio SDKs\\DIA Sdk\\lib;c:\\vctools\\Visual Studio SDKs\\BSC Sdk\\lib**  
**新 LIB 变量是：c:\\mylib;c:\\yourlib**   
## .NET Framework 等效项  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [环境常量](../../c-runtime-library/environmental-constants.md)   
 [\_putenv、\_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [\_dupenv\_s、\_wdupenv\_s](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md)