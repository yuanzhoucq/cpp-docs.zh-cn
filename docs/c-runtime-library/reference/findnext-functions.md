---
title: "_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfindnext"
  - "_findnext"
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
  - "findnext"
  - "_wfindnext32i64"
  - "_tfindnext64i32"
  - "findnext32"
  - "findnext32i64"
  - "wfindnext64i32"
  - "_wfindnext"
  - "tfindnext64"
  - "findnexti64"
  - "_findnexti64"
  - "_tfindnexti64"
  - "_findnext64i32"
  - "tfindnexti64"
  - "tfindnext32"
  - "_wfindnext64i32"
  - "findnext64i32"
  - "_findnext"
  - "_tfindnext32i64"
  - "_wfindnext64"
  - "wfindnext"
  - "wfindnext32"
  - "tfindnext32i64"
  - "_findnext64"
  - "_tfindnext64"
  - "_wfindnext32"
  - "findnext64"
  - "_findnext32i64"
  - "tfindnext"
  - "wfindnexti64"
  - "tfindnext64i32"
  - "_tfindnext32"
  - "wfindnext32i64"
  - "wfindnext64"
  - "_wfindnexti64"
  - "_tfindnext"
  - "_findnext32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wfindnexti64 函数"
  - "_tfindnext32 函数"
  - "wfindnexti64 函数"
  - "_wfindnext32i64 函数"
  - "findnext32i64 函数"
  - "tfindnext64i32 函数"
  - "_tfindnext64i32 函数"
  - "_findnext 函数"
  - "findnext64i32 函数"
  - "_tfindnext 函数"
  - "findnext32 函数"
  - "tfindnext32 函数"
  - "_findnext32 函数"
  - "_tfindnext32i64 函数"
  - "_wfindnext 函数"
  - "tfindnext 函数"
  - "_findnext64 函数"
  - "findnext64 函数"
  - "_findnext64i32 函数"
  - "wfindnext32i64 函数"
  - "findnext 函数"
  - "wfindnext32 函数"
  - "_wfindnext64i32 函数"
  - "findnexti64 函数"
  - "_wfindnext64 函数"
  - "_findnext32i64 函数"
  - "_findnexti64 函数"
  - "_tfindnext64 函数"
  - "wfindnext64i32 函数"
  - "tfindnexti64 函数"
  - "wfindnext64 函数"
  - "wfindnext 函数"
  - "tfindnext64 函数"
  - "_wfindnext32 函数"
  - "tfindnext32i64 函数"
  - "_tfindnexti64 函数"
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果有，则查找下一名称，对比之前调用[\_findfirst](../../c-runtime-library/reference/findfirst-functions.md)的`filespec` 参数，然后修改 `fileinfo` 结构的内容。  
  
## 语法  
  
```  
int _findnext(  
   intptr_t handle,  
   struct _finddata_t *fileinfo   
);  
int _findnext32(  
   intptr_t handle,  
   struct _finddata32_t *fileinfo   
);  
int _findnext64(  
   intptr_t handle,  
   struct __finddata64_t *fileinfo   
);  
int _findnexti64(  
   intptr_t handle,  
   struct __finddatai64_t *fileinfo   
);  
int _findnext32i64(  
   intptr_t handle,  
   struct _finddata32i64_t *fileinfo   
);  
int _findnext64i32(  
   intptr_t handle,  
   struct _finddata64i32_t *fileinfo   
);  
int _wfindnext(  
   intptr_t handle,  
   struct _wfinddata_t *fileinfo   
);  
int _wfindnext32(  
   intptr_t handle,  
   struct _wfinddata32_t *fileinfo   
);  
int _wfindnext64(  
   intptr_t handle,  
   struct _wfinddata64_t *fileinfo   
);  
int _wfindnexti64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext32i64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext64i32(  
   intptr_t handle,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### 参数  
 `handle`  
 搜索句柄返回上一调用到 `_findfirst`。  
  
 `fileinfo`  
 文件信息缓冲区。  
  
## 返回值  
 如果成功，则返回 0 。  否则，返回 \-1 并设置指示失败的特性值为 `errno`。  在下表中显示可能的错误代码。  
  
 `EINVAL`  
 无效参数 `fileinfo` 为`NULL`。  或者，操作系统返回无法预料的错误。  
  
 `ENOENT`  
 没有更多的匹配文件可以找到。  
  
 `ENOMEM`  
 没有足够的内存或文件名长度超过 `MAX_PATH`。  
  
 如果传递的是无效参数，则这些函数调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  
  
## 备注  
 在完成使用 `_findfirst` 或 `_findnext` 函数后（或任何变量），必须调用 [\_findclose](../../c-runtime-library/reference/findclose.md)。  这将释放在你的应用程序中使用这些函数的资源。  
  
 带有 `w` 前缀的这些函数变量是宽字符版本；否则，它们与对应的单字节函数相同。  
  
 这些函数的变量支持 32 位或 64 位时间类型和 32 位或 64 位文件大小。  第一个数字后缀 \(`32` 或 `64`\) 指示使用的时间类型的大小；第二个后缀要么是 `i32` 要么是 `i64`，指示文件大小是否表示为 32 位或 64 位整数。  有关哪些版本支持 32 位和 64 位时间类型和文件大小的详细信息，请参阅下表。  使用 64 位时间类型的变量允许文件创建日期表示为 23:59:59, December 31, 3000, UTC；因而使用 32 位时间类型只通过 19:14:07 January 18, 2038, UTC 表示日期。  1970 年 1 月 1 日 00:00:00，是所有这些函数的下限的日期范围。  
  
 除非出于特定原因需要使用显式指定时间范围的版本，使用 `_findnext` 或 `_wfindnext`，或者，如果需要支持大于3 GB的文件大小，请使用 `_findnexti64` 或 `_wfindnexti64`。  所有这些函数使用 64 位时间类型。  在以前版本的中，这些函数使用了 32 位时类型。  如果这是应用程序的重大更改，您可能定义 `_USE_32BIT_TIME_T` 获取旧行为。  如果定义 `_USE_32BIT_TIME_T` ，`_findnext`、`_finnexti64` 和它们对应的 Unicode 版本使用 32 位时间。  
  
### \_findnext 的时间类型和文件长度键入变量  
  
|函数|已定义 `_USE_32BIT_TIME_T`？|时间类型|文件长度类型|  
|--------|------------------------------|----------|------------|  
|`_findnext`, `_wfindnext`|未定义|64 位|32 位|  
|`_findnext`, `_wfindnext`|已定义|32 位|32 位|  
|`_findnext32`, `_wfindnext32`|不受定义宏影响|32 位|32 位|  
|`_findnext64`, `_wfindnext64`|不受定义宏影响|64 位|64 位|  
|`_findnexti64`, `_wfindnexti64`|未定义|64 位|64 位|  
|`_findnexti64`, `_wfindnexti64`|已定义|32 位|64 位|  
|`_findnext32i64`, `_wfindnext32i64`|不受定义宏影响|32 位|64 位|  
|`_findnext64i32`, `_wfindnext64i32`|不受定义宏影响|64 位|32 位|  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfindnext`|`_findnext`|`_findnext`|`_wfindnext`|  
|`_tfindnext32`|`_findnext32`|`_findnext32`|`_wfindnext32`|  
|`_tfindnext64`|`_findnext64`|`_findnext64`|`_wfindnext64`|  
|`_tfindnexti64`|`_findnexti64`|`_findnexti64`|`_wfindnexti64`|  
|`_tfindnext32i64`|`_findnext32i64`|`_findnext32i64`|`_wfindnext32i64`|  
|`_tfindnext64i32`|`_findnext64i32`|`_findnext64i32`|`_wfindnext64i32`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_findnext`|\<io.h\>|  
|`_findnext32`|\<io.h\>|  
|`_findnext64`|\<io.h\>|  
|`_findnexti64`|\<io.h\>|  
|`_findnext32i64`|\<io.h\>|  
|`_findnext64i32`|\<io.h\>|  
|`_wfindnext`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext32`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnexti64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext32i64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext64i32`|\<io.h\> or \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [系统调用](../../c-runtime-library/system-calls.md)   
 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md)