---
title: "_searchenv_s、_wsearchenv_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsearchenv_s"
  - "_searchenv_s"
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
  - "_searchenv_s"
  - "_wsearchenv_s"
  - "wsearchenv_s"
  - "searchenv_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_searchenv_s 函数"
  - "_tsearchenv_s 函数"
  - "_wsearchenv_s 函数"
  - "缓冲区溢出"
  - "缓冲区 [C++], 避免溢出"
  - "缓冲区 [C++], 缓冲区溢出"
  - "环境路径"
  - "环境路径, 搜索文件"
  - "文件 [C++], 查找"
  - "searchenv_s 函数"
  - "tsearchenv_s 函数"
  - "wsearchenv_s 函数"
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _searchenv_s、_wsearchenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用环境路径搜索文件。  正 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，[\_searchenv, \_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)版本的安全性得以增强。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char *pathname,  
   size_t numberOfElements  
);  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### 参数  
 \[in\] `filename`  
 要搜索的资源名称。  
  
 \[in\] `varname`  
 搜索的环境。  
  
 \[out\] `pathname`  
 缓冲存储完整路径。  
  
 \[in\] `numberOfElements`  
 `pathname`缓冲区的大小。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
 如果 `filename` 为空字符串，返回值为`ENOENT`。  
  
### 错误情况  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|返回值|`pathname` 的内容|  
|----------------|---------------|----------------|------------------------|---------|--------------------|  
|any|any|`NULL`|any|`EINVAL`|无|  
|`NULL`|any|any|any|`EINVAL`|不更改|  
|any|any|any|\<\= 0|`EINVAL`|不更改|  
  
 如果任一错误状态发生，调用无效参数句柄，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`EINVAL`。  
  
## 备注  
 `_searchenv_s` 程序在指定区域搜索目标文件。  `varname` 变量可以是任意环境或用户定义的用来指定目录路径列表的变量，例如 `PATH`、`LIB`和 `INCLUDE`。  由于 `_searchenv_s` 区分大小写，`varname` 应与环境变量的大小写相符。  如果 `varname` 不匹配进程环境中定义的环境变量名称，则该函数返回零，而 `pathname` 变量保持不变。  
  
 程序首先搜索当前工作目录中的文件。  如果它没有找到文件，它通过环境变量指定的目录查找下一个。  如果目标文件在这些目录之中，新创建的路径复制到 `pathname`。  如果找不到 `filename` 文件，`pathname` 包含一个空 null 终止的字符串。  
  
 `pathname` 缓冲区长度至少和 `_MAX_PATH` 字符长度一样，满足构造路径名的全长。  否则，`_searchenv_s` 可能会超过 `pathname` 缓冲区导致意外行为。  
  
 `_wsearchenv_s` 是 `_searchenv_s` 的宽字符版本；`_wsearchenv_s` 的参数是宽字符字符串。  否则`_wsearchenv_s` 和 `_searchenv_s` 行为相同,。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_searchenv_s`|\<stdlib.h\>|  
|`_wsearchenv_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_searchenv_s.c  
/* This program searches for a file in  
 * a directory specified by an environment variable.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
   errno_t err;  
  
   /* Search for file in PATH environment variable: */  
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );  
   if (err != 0)  
   {  
      printf("Error searching the path. Error code: %d\n", err);  
   }  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
  **CL.EXE 的路径：**  
**C:\\Program Files\\Microsoft Visual Studio 2010\\VC\\BIN\\CL.EXE**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [目录控制](../../c-runtime-library/directory-control.md)   
 [\_searchenv、\_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_putenv、\_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)