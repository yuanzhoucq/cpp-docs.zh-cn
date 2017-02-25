---
title: "_getcwd_dbg、_wgetcwd_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wgetcwd_dbg"
  - "_getcwd_dbg"
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
  - "_getcwd_dbg"
  - "_wgetcwd_dbg"
  - "getcwd_dbg"
  - "wgetcwd_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getcwd_dbg 函数"
  - "_wgetcwd_dbg 函数"
  - "当前工作目录"
  - "[C++], 当前工作"
  - "getcwd_dbg 函数"
  - "wgetcwd_dbg 函数"
  - "工作目录"
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _getcwd_dbg、_wgetcwd_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md) 函数的调试版本（仅在调试过程中可用）。  
  
## 语法  
  
```  
char *_getcwd_dbg(     char *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wgetcwd_dbg(     wchar_t *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 参数  
 `buffer`  
 路径的存储位置。  
  
 `maxlen`  
 路径的最大长度（以字符为单位）：`_getcwd_dbg` 的 `char` 和 `_wgetcwd_dbg` 的 `wchar_t`。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
## 返回值  
 返回指向 `buffer` 的指针。  `NULL` 返回值指示错误，并将 `errno` 设置为 `ENOMEM`，指示内存不足，无法分配 `maxlen` 个字节（当将 `NULL` 参数给定为 `buffer` 时），或设置为 `ERANGE`，指示该路径长于 `maxlen` 个字符。  
  
 有关详细信息，请参见[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_getcwd_dbg` 和 `_wgetcwd_dbg` 函数与 `_getcwd` 和 `_wgetcwd` 完全相同，只是当定义 \_`DEBUG` 时，如果将 `NULL` 作为第一个参数进行传递，则这些函数将使用 `malloc` 的调试版本和 `_malloc_dbg` 来分配内存。  有关详细信息，请参见[\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。  可以改为定义 `_CRTDBG_MAP_ALLOC` 标志。  定义 `_CRTDBG_MAP_ALLOC` 后，对 `_getcwd`和 `_wgetcwd`的调用将分别重新映射到 `_getcwd_dbg`和 `_wgetcwd_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。  因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。  有关详细信息，请参见[调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
## 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetcwd_dbg`|`_getcwd_dbg`|`_getcwd_dbg`|`_wgetcwd_dbg`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_getcwd_dbg`|\<crtdbg.h\>|  
|`_wgetcwd_dbg`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 <xref:System.Environment.CurrentDirectory%2A>  
  
## 请参阅  
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [目录控制](../../c-runtime-library/directory-control.md)   
 [堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)