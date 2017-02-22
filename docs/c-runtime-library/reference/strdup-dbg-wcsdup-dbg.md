---
title: "_strdup_dbg、_wcsdup_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdup_dbg"
  - "_wcsdup_dbg"
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
  - "_wcsdup_dbg"
  - "strdup_dbg"
  - "_strdup_dbg"
  - "wcsdup_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strdup_dbg 函数"
  - "_wcsdup_dbg 函数"
  - "复制字符串"
  - "重复字符串"
  - "stdup_dbg 函数"
  - "字符串 [C++], 复制"
  - "字符串 [C++], 复制"
  - "wcsdup_dbg 函数"
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _strdup_dbg、_wcsdup_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 `malloc` 的调试版本的 [\_strdup and \_wcsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) 的版本。  
  
## 语法  
  
```  
char *_strdup_dbg(    const char *strSource,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wcsdup_dbg(    const wchar_t *strSource,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 参数  
 `strSource`  
 null 终止的源字符串。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 NULL。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 NULL。  
  
## 返回值  
 如果无法分配存储，则其中每个函数都将返回一个指向复制字符串的存储位置的指针或 `NULL`。  
  
## 备注  
 `_strdup_dbg` 和 `_wcsdup_dbg` 函数与 `_strdup` 和 `_wcsdup` 完全相同，只是当定义 `_DEBUG` 时，这些函数将使用 `malloc` 的调试版本和 `_malloc_dbg` 来为复制的字符串分配内存。  有关 `_malloc_dbg` 的调试功能的信息，请参阅 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。  可以改为定义标志 `_CRTDBG_MAP_ALLOC`。  定义 `_CRTDBG_MAP_ALLOC` 后，对 `_strdup` 和 `_wcsdup` 的调用将分别重新映射到 `_strdup_dbg` 和 `_wcsdup_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。  因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。  有关块类型的详细信息，请参阅[调试堆中的块类型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有调试版本。  
  
## .NET Framework 等效项  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strdup、\_wcsdup、\_mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [堆分配函数的“Debug”版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)