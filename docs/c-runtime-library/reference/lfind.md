---
title: "_lfind | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lfind
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
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind
- _lfind
dev_langs: C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930a8ebf26be12bdaa5b596578c28a7b1adcf574
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="lfind"></a>_lfind
用于针对指定的键执行线性搜索。 此函数有一个更安全的版本；请参阅 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 指向搜索数据的基项的指针。  
  
 `num`  
 数组元素的数目。  
  
 `width`  
 数组元素的宽度。  
  
 `compare`  
 指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。  
  
## <a name="return-value"></a>返回值  
 如果找到此键，则 `_lfind` 返回指向 `base` 处的与 `key` 匹配的数组元素的指针。 如果未找到该键，则 `_lfind` 返回 `NULL`。  
  
## <a name="remarks"></a>备注  
 `_lfind` 函数对 `num` 元素的数组中的值 `key` 执行线性搜索，每个元素为 `width` 字节。 与 `bsearch` 不同，`_lfind` 不要求对数组进行排序。 参数 `base` 是指向待搜索数组基项的指针。 参数 `compare` 是指向用户提供的例程的指针，它比较两个数组元素，然后返回指定它们关系的值。 `_lfind` 在搜索过程中一次或多次调用 `compare` 例程，将指针传递给每个调用上的两个数组元素。 `compare` 例程必须比较这些元素，然后返回非零值（表示元素不同）或 0（表示元素相同）。  
  
 此函数验证其参数。 如果 `compare`、`key` 或 `num` 为 `NULL`，或者如果 `base` 为 NULL 且 *`num` 不为零，或者如果 `width` 小于零，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_lfind`|\<search.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Hello found  
```  
  
## <a name="see-also"></a>请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)