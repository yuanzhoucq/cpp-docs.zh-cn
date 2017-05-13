---
title: "qsort | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- qsort
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b71bdc6b2b2bff50645a7ce8ae1ef88ad4d6dd91
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="qsort"></a>qsort
执行快速排序。 此函数有一个更安全的版本；请参阅 [qsort_s](../../c-runtime-library/reference/qsort-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>参数  
 `base`  
 目标数组的开头。  
  
 `num`  
 元素中的数组大小。  
  
 `width`  
 元素大小（字节）。  
  
 `compare`  
 指向用户提供的例程的指针比较两个数组元素，并返回指定它们关系的值。  
  
## <a name="remarks"></a>备注  
 `qsort` 函数实现了一种快速排序算法，对数组中的 `num` 元素（每个元素大小为 `width` 字节）进行排序。 参数 `base` 是指向待排序数组的基项的指针。 `qsort` 使用已排序的元素覆盖此数组。  
  
 `qsort` 在排序过程中一次或多次调用 `compare` 例程，并将指针传递给每个调用中的两个数组元素。  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 该例程将比较元素，并返回下列值之一。  
  
|比较函数返回值|描述|  
|-----------------------------------|-----------------|  
|< 0|`elem1` 小于 `elem2`|  
|0|`elem1` 等效于 `elem2`|  
|> 0|`elem1` 大于 `elem2`|  
  
 数组按比较函数中定义的升序进行排序。 若要以降序对数组进行排序，请反转比较函数中的“大于”和“小于”的意义。  
  
 此函数验证其参数。 如果 `compare` 或 `num` 为 `NULL`，或者，如果 `base` 为 `NULL` 且 *`num` 不为零，亦或者，如果 `width` 小于零，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则返回函数并将 `errno` 设置为 `EINVAL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`qsort`|\<stdlib.h> 和 \<search.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
boy deserves every favor good  
```  
  
## <a name="see-also"></a>另请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)
