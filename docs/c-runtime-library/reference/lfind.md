---
title: "_lfind | Microsoft Docs"
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
  - "_lfind"
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
  - "lfind"
  - "_lfind"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lfind 函数"
  - "数组 [CRT], 搜索"
  - "在数组中查找密钥"
  - "lfind 函数"
  - "线性搜索"
  - "搜索, 线性"
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lfind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Performs a linear search for the specified key.  A more secure version of this function is available; see [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md).  
  
## 语法  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### 参数  
 `key`  
 Object to search for.  
  
 `base`  
 Pointer to the base of search data.  
  
 `num`  
 Number of array elements.  
  
 `width`  
 Width of array elements.  
  
 `compare`  
 Pointer to comparison routine.  The first parameter is a pointer to key for search.  The second parameter is a pointer to array element to be compared with key.  
  
## 返回值  
 If the key is found, `_lfind` returns a pointer to the element of the array at `base` that matches `key`.  If the key is not found, `_lfind` returns `NULL`.  
  
## 备注  
 The `_lfind` function performs a linear search for the value `key` in an array of `num` elements, each of `width` bytes.  Unlike `bsearch`, `_lfind` does not require the array to be sorted.  The `base` argument is a pointer to the base of the array to be searched.  The `compare` argument is a pointer to a user\-supplied routine that compares two array elements and then returns a value specifying their relationship.  `_lfind` calls the `compare` routine one or more times during the search, passing pointers to two array elements on each call.  The `compare` routine must compare the elements and then return nonzero \(meaning the elements are different\) or 0 \(meaning the elements are identical\).  
  
 此函数验证其参数。  If `compare`, `key` or `num` is `NULL`, or if `base` is NULL and \*`num` is nonzero, or if `width` is less than zero, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lfind`|\<search.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_lfind.c  
// This program uses _lfind to search a string array  
// for an occurrence of "hello".  
  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
  
int main( )  
{  
   char *arr[] = {"Hi", "Hello", "Bye"};  
   int n = sizeof(arr) / sizeof(char*);  
   char **result;  
   char *key = "hello";  
  
   result = (char **)_lfind( &key, arr,   
                      &n, sizeof(char *), compare );  
  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "hello not found!\n" );  
}  
```  
  
  **Hello found**   
## .NET Framework 等效项  
 [System::Collections::ArrayList::Contains](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)