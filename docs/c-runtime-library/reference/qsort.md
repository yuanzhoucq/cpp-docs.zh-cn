---
title: "qsort | Microsoft Docs"
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
  - "qsort"
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
  - "qsort"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "qsort 函数"
  - "快速排序算法"
  - "对数组进行排序"
  - "数组 [CRT]，排序"
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行快速排序。  提供该函数的一个更安全版本；请参阅 [qsort\_s](../../c-runtime-library/reference/qsort-s.md)。  
  
## 语法  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### 参数  
 `base`  
 目标数组的开头。  
  
 `num`  
 元素的数组大小。  
  
 `width`  
 以字节为单位的元素大小。  
  
 `compare`  
 给比较两个数组的元素并返回值指定这些关系的一个用户提供的实例的指针。  
  
## 备注  
 `qsort` 函数可实现快速排序算法对一个 `num` 元素，每个 `width` 字节数组进行排序。  参数 `base` 是一个指向要排序数组的基类的指针。  使用`qsort` 覆盖元素的排序，此数组。  
  
 在排序时，`qsort` 调用程序 `compare` 一次或多次，并在每次调用时将指针传给两个数组元素：  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 比较例程元素并返回下列值之一。  
  
|比较函数返回值|说明|  
|-------------|--------|  
|\< 0|`elem1` 小于 `elem2`|  
|0|`elem1` 等效于 `elem2`|  
|\> 0|`elem1` 大于 `elem2`|  
  
 正如所定义的比较函数，数组以递增排序。  若要降序排序一个数组，在比较函数中反转“大于”和“小于“的意思。  
  
 此函数验证其参数。  如果 `compare`、`num` 或 `NULL` 是 `base`，或 `NULL`为 NULL 和" \*`num` 不为零，或者，如果 `width` 小于零，无效参数处理程序将被调用，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`qsort`|\<stdlib.h\> and \<search.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_qsort.c  
// arguments: every good boy deserves favor  
  
/* This program reads the command-line  
 * parameters and uses qsort to sort them. It  
 * then displays the sorted arguments.  
 */  
  
#include <stdlib.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main( int argc, char **argv )  
{  
   int i;  
   /* Eliminate argv[0] from sort: */  
   argv++;  
   argc--;  
  
   /* Sort remaining args using Quicksort algorithm: */  
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );  
  
   /* Output sorted list: */  
   for( i = 0; i < argc; ++i )  
      printf( " %s", argv[i] );  
   printf( "\n" );  
}  
  
int compare( const void *arg1, const void *arg2 )  
{  
   /* Compare all of both strings: */  
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );  
}  
```  
  
  **男孩需要每天喜爱**   
## .NET Framework 等效项  
 [System::Collections::ArrayList::Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)  
  
## 请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)