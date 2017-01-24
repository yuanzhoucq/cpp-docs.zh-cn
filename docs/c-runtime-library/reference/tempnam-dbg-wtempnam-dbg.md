---
title: "_tempnam_dbg、_wtempnam_dbg | Microsoft Docs"
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
  - "_wtempnam_dbg"
  - "_tempnam_dbg"
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
  - "wtempnam_dbg"
  - "tempnam_dbg"
  - "_tempnam_dbg"
  - "_wtempnam_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tempnam_dbg 函数"
  - "_wtempnam_dbg 函数"
  - "文件名 [C++], 创建临时"
  - "文件名 [C++], 临时"
  - "tempnam_dbg 函数"
  - "临时文件, 创建"
  - "wtempnam_dbg 函数"
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tempnam_dbg、_wtempnam_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 `malloc, _malloc_dbg` 的调试版本的 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 的函数版本。  
  
## 语法  
  
```  
char *_tempnam_dbg(    const char *dir,    const char *prefix,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wtempnam_dbg(    const wchar_t *dir,    const wchar_t *prefix,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 参数  
 `dir`  
 文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。  
  
 `prefix`  
 将在由 `_tempnam` 返回的名称前面附加的字符串。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK`或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
## 返回值  
 如果发生失败，则每个函数均返回一个指向生成的名称的指针或 `NULL`。  如果在 TMP 环境变量和 `dir` 参数中指定的目录名称无效，则可能发生失败。  
  
> [!NOTE]
>  对于由 `_tempnam_dbg` 和 `_wtempnam_dbg` 分配的指针，必须调用 `free`（或 `free_dbg`）。  
  
## 备注  
 `_tempnam_dbg` 和 `_wtempnam_dbg`函数与 `_tempnam`和 `_wtempnam`完全相同，只是当定义 `_DEBUG`时，如果将 `NULL` 作为第一个参数进行传递，则这些函数将使用 `malloc` 的调试版本和 `_malloc_dbg` 来分配内存。  有关详细信息，请参见[\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。  可以改为定义标志 `_CRTDBG_MAP_ALLOC`。  定义 `_CRTDBG_MAP_ALLOC` 后，对 `_tempnam` 和 `_wtempnam` 的调用将分别重新映射到  `_tempnam_dbg` 和 `_wtempnam_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。  因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。  有关详细信息，请参见[调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_ttempnam_dbg`|`_tempnam_dbg`|`_tempnam_dbg`|`_wtempnam_dbg`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_tempnam_dbg`, `_wtempnam_dbg`|\<crtdbg.h\>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)