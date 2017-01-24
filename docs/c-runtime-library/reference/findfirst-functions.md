---
title: "_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 | Microsoft Docs"
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
  - "_findfirst"
  - "_wfindfirst"
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
  - "findfirst32i64"
  - "wfindfirst32i64"
  - "tfindfirst64"
  - "_findfirst64i32"
  - "_wfindfirst32i64"
  - "_wfindfirsti64"
  - "wfindfirst"
  - "_tfindfirsti64"
  - "findfirst32"
  - "_tfindfirst32"
  - "_findfirsti64"
  - "findfirst"
  - "wfindfirst64"
  - "wfindfirst32"
  - "tfindfirst32"
  - "_wfindfirst64i32"
  - "findfirst64i32"
  - "tfindfirst64i32"
  - "_wfindfirst"
  - "findfirsti64"
  - "_findfirst32i64"
  - "wfindfirst64i32"
  - "_wfindfirst32"
  - "_findfirst32"
  - "_tfindfirst32i64"
  - "tfindfirst"
  - "_tfindfirst64i32"
  - "findfirst64"
  - "_tfindfirst"
  - "_findfirst64"
  - "_tfindfirst64"
  - "tfindfirst32i64"
  - "_findfirst"
  - "_wfindfirst64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tfindfirst64 函数"
  - "_wfindfirst64i32 函数"
  - "_wfindfirst32i64 函数"
  - "wfindfirst32 函数"
  - "_findfirst 函数"
  - "wfindfirst64 函数"
  - "_wfindfirst 函数"
  - "_findfirst64i32 函数"
  - "wfindfirst 函数"
  - "_findfirst64 函数"
  - "tfindfirst32 函数"
  - "_tfindfirst64i32 函数"
  - "findfirst 函数"
  - "findfirst32i64 函数"
  - "tfindfirst64 函数"
  - "_tfindfirst32 函数"
  - "tfindfirst32i64 函数"
  - "tfindfirst64i32 函数"
  - "_wfindfirsti64 函数"
  - "_findfirst32i64 函数"
  - "findfirst32 函数"
  - "findfirsti64 函数"
  - "findfirst64i32 函数"
  - "tfindfirsti64 函数"
  - "tfindfirst 函数"
  - "_wfindfirst32 函数"
  - "wfindfirsti64 函数"
  - "_tfindfirsti64 函数"
  - "_tfindfirst 函数"
  - "_tfindfirst32i64 函数"
  - "findfirst64 函数"
  - "_findfirst32 函数"
  - "_findfirsti64 函数"
  - "wfindfirst32i64 函数"
  - "wfindfirst64i32 函数"
  - "_wfindfirst64 函数"
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供有关与 `filespec` 参数中指定的文件 filename 的实例的信息。  
  
## 语法  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### 参数  
 `filespec`  
 目标文件规范 \(可以包括通配符\)。  
  
 `fileinfo`  
 文件信息缓冲区。  
  
## 返回值  
 如果成功，则 `_findfirst` 返回标识匹配 `filespec` 规范，可在后续调用到 [\_findnext](../../c-runtime-library/reference/findnext-functions.md) 或 `_findclose`文件的或组的搜索单个处理。  否则，`_findfirst` 返回 \- 1 并将 `errno` 设置为以下值之一。  
  
 `EINVAL`  
 无效参数 `filespec` 或 `fileinfo`为`NULL`。  或者，操作系统返回无法预料的错误。  
  
 `ENOENT`  
 不能匹配的文件大小。  
  
 `ENOMEM`  
 内存不足。  
  
 `EINVAL`  
 无效文件名规范或给定的文件名大于 `MAX_PATH`。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果传递的是无效参数，则这些函数调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  
  
## 备注  
 在完成使用 `_findfirst` 或 `_findnext` 函数后（或任何变量），必须调用 [\_findclose](../../c-runtime-library/reference/findclose.md)。  这将释放在你的应用程序中使用这些函数的资源。  
  
 带有 `w` 前缀的这些函数变量是宽字符版本；否则，它们与对应的单字节函数相同。  
  
 这些函数的变量支持 32 位或 64 位时间类型和 32 位或 64 位文件大小。  第一个数字后缀 \(`32` 或 `64`\) 指示使用的时间类型的大小；第二个后缀要么是 `i32` 要么是 `i64`，指示文件大小是否表示为 32 位或 64 位整数。  有关哪些版本支持 32 位和 64 位时间类型和文件大小的详细信息，请参阅下表。  `i32` 或 `i64` 后缀省略，如果相同时间类型的范围，因此，`_findfirst64` 还支持 64 位文件长度，`_findfirst32` 仅支持 32 位文件长度。  
  
 这些函数为 `fileinfo` 参数使用大量 `_finddata_t` 结构。  有关 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md) 类的更多信息，请参见。  
  
 使用 64 位时类型的变体允许通过 23:59 将表示的文件创建日期：59，3000 年 12 月 31 日，UTC。  使用 32 位时类型的那些通过 19:14 只表示日期：07 年 1 月 18 日 2038 年，UTC。  1970 年 1 月 1 日 00:00:00，是所有这些函数的下限的日期范围。  
  
 除非出于特定原因需要使用显式指定时间范围的版本，使用 `_findfirst` 或 `_wfindfirst`，或者，如果需要支持大于3 GB的文件大小，请使用 `_findfirsti64` 或 `_wfindfirsti64`。  所有这些函数使用 64 位时间类型。  在早期版本中，这些函数使用了 32 位时类型。  如果这是应用程序的重大更改，您可能定义 `_USE_32BIT_TIME_T` 获取旧行为。  如果定义 `_USE_32BIT_TIME_T` ，`_findfirst`、`_finfirsti64` 和它们对应的 Unicode 版本使用 32 位时间。  
  
### \_findnext 的时间类型和文件长度键入变量  
  
|函数|已定义 `_USE_32BIT_TIME_T`？|时间类型|文件长度类型|  
|--------|------------------------------|----------|------------|  
|`_findfirst`, `_wfindfirst`|未定义|64 位|32 位|  
|`_findfirst`, `_wfindfirst`|已定义|32 位|32 位|  
|`_findfirst32`, `_wfindfirst32`|不受定义宏影响|32 位|32 位|  
|`_findfirst64`, `_wfindfirst64`|不受定义宏影响|64 位|64 位|  
|`_findfirsti64`, `_wfindfirsti64`|未定义|64 位|64 位|  
|`_findfirsti64`, `_wfindfirsti64`|已定义|32 位|64 位|  
|`_findfirst32i64`, `_wfindfirst32i64`|不受定义宏影响|32 位|64 位|  
|`_findfirst64i32`, `_wfindfirst64i32`|不受定义宏影响|64 位|32 位|  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_findfirst`|\<io.h\>|  
|`_findfirst32`|\<io.h\>|  
|`_findfirst64`|\<io.h\>|  
|`_findfirsti64`|\<io.h\>|  
|`_findfirst32i64`|\<io.h\>|  
|`_findfirst64i32`|\<io.h\>|  
|`_wfindfirst`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst32`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirsti64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst32i64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst64i32`|\<io.h\> or \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::IO::DirectoryInfo::GetFiles](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)  
  
## 请参阅  
 [系统调用](../../c-runtime-library/system-calls.md)   
 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md)