---
title: "_lsearch_s | Microsoft Docs"
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
  - "_lsearch_s"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_lsearch_s"
  - "lsearch_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lsearch_s 函数"
  - "数组 [CRT], 搜索"
  - "键, 在数组中查找"
  - "线性搜索"
  - "lsearch_s 函数"
  - "搜索, 线性"
  - "values, 搜索"
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lsearch_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Performs a linear search for a value.  A version of [\_lsearch](../../c-runtime-library/reference/lsearch.md) with security enhancements as described in [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md).  
  
## 语法  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### 参数  
 `key`  
 Object to search for.  
  
 `base`  
 Pointer to the base of array to be searched.  
  
 `num`  
 Number of elements.  
  
 `size`  
 Size of each array element in bytes.  
  
 `compare`  
 Pointer to the comparison routine.  The second parameter is a pointer to the key for search.  The third parameter is a pointer to an array element to be compared with the key.  
  
 `context`  
 A pointer to an object that might be accessed in the comparison function.  
  
## 返回值  
 If `key` is found, `_lsearch_s` returns a pointer to the element of the array at `base` that matches `key`.  If `key` is not found, `_lsearch_s` returns a pointer to the newly added item at the end of the array.  
  
 If invalid parameters are passed to the function, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  If execution is allowed to continue, then `errno` is set to `EINVAL` and the function returns `NULL`.  有关更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 错误情况  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|零|`EINVAL`|  
|any|any|`NULL`|an|any|`EINVAL`|  
  
## 备注  
 The `_lsearch_s` function performs a linear search for the value `key` in an array of `num` elements, each of `width` bytes.  Unlike `bsearch_s`, `_lsearch_s` does not require the array to be sorted.  If `key` is not found, then `_lsearch_s` adds it to the end of the array and increments `num`.  
  
 The `compare` function is a pointer to a user\-supplied routine that compares two array elements and returns a value specifying their relationship.  The `compare` function also takes the pointer to the context as the first argument.  `_lsearch_s` calls `compare` one or more times during the search, passing pointers to two array elements on each call.  `compare` must compare the elements and then return either nonzero \(meaning the elements are different\) or 0 \(meaning the elements are identical\).  
  
 The `context` pointer can be useful if the searched data structure is part of an object and the `compare` function needs to access members of the object.  For example, code in the `compare` function can cast the void pointer into the appropriate object type and access members of that object.  The addition of the `context` pointer makes `_lsearch_s` more secure because additional context can be used to avoid reentrancy bugs associated with using static variables to make data available to the `compare` function.  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lsearch_s`|\<search.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)