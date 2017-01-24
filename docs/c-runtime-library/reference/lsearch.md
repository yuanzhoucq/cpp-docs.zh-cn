---
title: "_lsearch | Microsoft Docs"
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
  - "_lsearch"
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
  - "_lsearch"
  - "lsearch"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lsearch 函数"
  - "数组 [CRT], 搜索"
  - "键, 在数组中查找"
  - "线性搜索"
  - "lsearch 函数"
  - "搜索, 线性"
  - "values, 搜索"
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lsearch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Performs a linear search for a value; adds to end of list if not found.  A more secure version of this function is available; see [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md).  
  
## 语法  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### 参数  
 `key`  
 Object to search for.  
  
 `base`  
 Pointer to the base of array to be searched.  
  
 `num`  
 Number of elements.  
  
 `width`  
 Width of each array element.  
  
 `compare`  
 Pointer to the comparison routine.  The first parameter is a pointer to the key for search.  The second parameter is a pointer to an array element to be compared with the key.  
  
## 返回值  
 If the key is found, `_lsearch` returns a pointer to the element of the array at `base` that matches `key`.  If the key is not found, `_lsearch` returns a pointer to the newly added item at the end of the array.  
  
## 备注  
 The `_lsearch` function performs a linear search for the value `key` in an array of `num` elements, each of `width` bytes.  Unlike `bsearch`, `_lsearch` does not require the array to be sorted.  If `key` is not found, `_lsearch` adds it to the end of the array and increments `num`.  
  
 The `compare` argument is a pointer to a user\-supplied routine that compares two array elements and returns a value specifying their relationship.  `_lsearch` calls the `compare` routine one or more times during the search, passing pointers to two array elements on each call.  `compare` must compare the elements and return either nonzero \(meaning the elements are different\) or 0 \(meaning the elements are identical\).  
  
 此函数验证其参数。  If `compare`, `key` or `num` is `NULL`, or if `base` is NULL and \*`num` is nonzero, or if `width` is less than zero, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lsearch`|\<search.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
  **在\_lsearch之前的单词表：你好 谢谢 再见**  
**wordlist after \_lsearch: hello thanks bye extra**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)