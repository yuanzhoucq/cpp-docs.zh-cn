---
title: "bsearch_s |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- bsearch_s
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
- bsearch_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1ec2b76d64f9a65d19362f592483490c8b9bb3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="bsearchs"></a>bsearch_s
执行排序数组的二进制搜索。 这是 [bsearch](../../c-runtime-library/reference/bsearch.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
void *bsearch_s(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 指向搜索数据的基项的指针。  
  
 `num`  
 元素数量。  
  
 `width`  
 元素的宽度。  
  
 `compare`  
 比较两个元素的回调函数。 第一个参数是 `context` 指针。 第二个参数是一个指向用于搜索的 `key` 的指针。 第三个参数是指向要与 `key`进行比较的数组元素的指针。  
  
 `context`  
 指向可在比较函数中访问的对象的指针。  
  
## <a name="return-value"></a>返回值  
 `bsearch_s` 返回一个指向 `base` 所指向数组中的 `key` 匹配项的指针。 如果未找到 `key` ，该函数将返回 `NULL`。 如果数组不是以升序排序的，或包含具有相同键的重复记录，则不可预知结果。  
  
 如果传递到此函数的参数无效，则将调用无效的参数处理程序，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>错误条件  
  
|||||||  
|-|-|-|-|-|-|  
|`key`|`base`|`compare`|`num`|`width`|`errno`|  
|`NULL`|任何|任何|任何|任何|`EINVAL`|  
|任何|`NULL`|任何|!= 0|任何|`EINVAL`|  
|任何|任何|任何|任何|= 0|`EINVAL`|  
|任何|任何|`NULL`|一个|任何|`EINVAL`|  
  
## <a name="remarks"></a>备注  
 `bsearch_s` 函数对 `num` 元素的已排序数组执行二进制搜索，每个元素的大小为 `width` 字节。 `base` 值是指向要搜索的数组的基项的指针，而 `key` 是要搜索的值。 `compare` 参数是指向用户提供的例程的指针，该例程将对请求的键与数组元素进行比较，并返回指定其关系的以下值之一：  
  
|`compare` 例程所返回的值|描述|  
|-----------------------------------------|-----------------|  
|\< 0|键小于数组元素。|  
|0|键等于数组元素。|  
|> 0|键大于数组元素。|  
  
 如果搜索的数据结构是对象的一部分，且比较函数需要访问该对象的成员，则 `context` 指针可能有用。 `compare` 函数可能会将 void 指针转换为适当的对象类型并访问该对象的成员。 添加 `context` 参数将使得 `bsearch_s` 更安全，因为其他上下文可用于避免重新进入 Bug 与使用静态变量以使数据对 `compare` 函数可用相关联。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`bsearch_s`|\<stdlib.h> 和 \<search.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 此程序对具有 [qsort_s](../../c-runtime-library/reference/qsort-s.md)的字符串数组进行排序，然后使用 bsearch_s 查找单词“cat”。  
  
```  
// crt_bsearch_s.cpp  
// This program uses bsearch_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
#define ENGLISH_LOCALE "English_US.850"  
#endif  
  
#ifdef CODEPAGE_1252  
#define ENGLISH_LOCALE "English_US.1252"  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, char **str1, char **str2)  
{  
    char *s1 = *str1;  
    char *s2 = *str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
  
   char *key = "cat";  
   char **result;  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort_s( arr,  
            sizeof(arr)/sizeof(arr[0]),  
            sizeof( char * ),  
            (int (*)(void*, const void*, const void*))compare,  
            &locale(ENGLISH_LOCALE) );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch_s( &key,  
                                arr,  
                                sizeof(arr)/sizeof(arr[0]),  
                                sizeof( char * ),  
                                (int (*)(void*, const void*, const void*))compare,  
                                &locale(ENGLISH_LOCALE) );  
   if( result )  
      printf( "\n%s found at %Fp\n", *result, result );  
   else  
      printf( "\nCat not found!\n" );  
}  
```  
  
```Output  
cat cow dog goat horse human pig rat  
cat found at 002F0F04  
```  
  
## <a name="see-also"></a>请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)