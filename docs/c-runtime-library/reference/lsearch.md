---
title: "_lsearch | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _lsearch
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
- _lsearch
- lsearch
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb4cb64b9287de11a894a8ca7c7cdd4490fcc446
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="lsearch"></a>_lsearch
对值执行线性搜索；如果未找到，则添加到列表的末尾。 提供此函数的一个更安全的版本；请参阅 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 指向要搜索的数组基的指针。  
  
 `num`  
 元素数量。  
  
 `width`  
 各个数组元素的宽度。  
  
 `compare`  
 指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。  
  
## <a name="return-value"></a>返回值  
 如果找到此键，则 `_lsearch` 返回指向 `base` 上的与 `key` 匹配的数组元素的指针。 如果未找到此键，则 `_lsearch` 返回指向数组末尾的新添加项的指针。  
  
## <a name="remarks"></a>备注  
 `_lsearch` 函数对 `num` 元素的数组中的值 `key` 执行线性搜索，每个元素为 `width` 字节。 与 `bsearch` 不同的是，`_lsearch` 不要求对数组进行排序。 如果未找到 `key`，`_lsearch` 会将其添加到数组末尾并增加 `num`。  
  
 参数 `compare` 是指向用户提供的例程的指针，它比较两个数组元素，并返回指定其关系的值。 `_lsearch` 在搜索过程中一次或多次调用 `compare` 例程，将指针传递给每个调用上的两个数组元素。 `compare` 必须比较这些元素，并返回非零值（表示元素不同）或 0（表示元素相同）。  
  
 此函数验证其参数。 如果 `compare`、`key` 或 `num` 为 `NULL`，或者如果 `base` 为 NULL 且 *`num` 不为零，或者如果 `width` 小于零，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_lsearch`|\<search.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
wordlist before _lsearch: hello thanks bye  
wordlist after _lsearch: hello thanks bye extra  
```  
  
## <a name="see-also"></a>请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)