---
title: "_lfind_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lfind_s
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
- lfind_s
- _lfind_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c50893f1dc73db9f928eaea346a381d1bd991d2f
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="lfinds"></a>_lfind_s
用于针对指定的键执行线性搜索。 这是一个 [_lfind](../../c-runtime-library/reference/lfind.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 指向搜索数据的基项的指针。  
  
 `num`  
 数组元素的数目。  
  
 `size`  
 以字节为单位的数组元素的大小。  
  
 `compare`  
 指向比较例程的指针。 第一个参数是 `context` 指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。  
  
 `context`  
 指向可能在比较函数中访问的对象的指针。  
  
## <a name="return-value"></a>返回值  
 如果找到此键，则 `_lfind_s` 返回指向 `base` 处的与 `key` 匹配的数组元素的指针。 如果未找到该键，则 `_lfind_s` 返回 `NULL`。  
  
 如果传递到此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。  
  
### <a name="error-conditions"></a>错误条件  
  
|密钥|base|compare|num|size|errno|  
|---------|----------|-------------|---------|----------|-----------|  
|`NULL`|任何|任何|任何|任何|`EINVAL`|  
|任何|`NULL`|任何|!= 0|任何|`EINVAL`|  
|任何|任何|任何|any|零|`EINVAL`|  
|any|任何|`NULL`|一个|任何|`EINVAL`|  
  
## <a name="remarks"></a>备注  
 `_lfind_s` 函数对 `num` 元素的数组中的值 `key` 执行线性搜索，每个元素为 `width` 字节。 与 `bsearch_s` 不同，`_lfind_s` 不要求对数组进行排序。 参数 `base` 是指向待搜索数组基项的指针。 参数 `compare` 是指向用户提供的例程的指针，它比较两个数组元素，然后返回指定它们关系的值。 `_lfind_s` 在搜索过程中调用一次或多次 `compare` 例程，将 `context` 指针和多个指针传递给每个调用上的两个数组元素。 `compare` 例程必须比较这些元素，然后返回非零值（表示元素不同）或 0（表示元素相同）。  
  
 `_lfind_s` 类似于 `_lfind`，除了添加指向比较函数的参数和函数参数列表的 `context` 指针。 如果搜索的数据结构是对象的一部分，且 `compare` 函数需要访问该对象的成员，则 `context` 指针可能有用。 `compare` 函数可能会将 void 指针转换为适当的对象类型并访问该对象的成员。 添加 `context` 参数将使 `_lfind_s` 更安全，因为其他上下文可用于避免使用静态变量以使数据对 `compare` 函数可用与重新进入 Bug 相关联。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_lfind_s`|\<search.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
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
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
```Output  
weit found  
```  
  
## <a name="see-also"></a>另请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort_s](../../c-runtime-library/reference/qsort-s.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)
