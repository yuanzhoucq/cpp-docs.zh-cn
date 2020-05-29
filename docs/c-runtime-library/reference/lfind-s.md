---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916508"
---
# <a name="_lfind_s"></a>_lfind_s

用于针对指定的键执行线性搜索。 这是一个 [_lfind](lfind.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。

## <a name="syntax"></a>语法

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>参数

*键*<br/>
要搜索的对象。

*base*<br/>
指向搜索数据的基项的指针。

*数字*<br/>
数组元素的数目。

size <br/>
以字节为单位的数组元素的大小。

*并排*<br/>
指向比较例程的指针。 第一个参数是*上下文*指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。

*上下文*<br/>
指向可在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

如果找到该密钥， **_lfind_s**将返回一个指针，该指针指向匹配*键*的*基*中的数组元素。 如果找不到该密钥， **_lfind_s**将返回**NULL**。

如果传递到函数的参数无效，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。

### <a name="error-conditions"></a>错误条件

|键|base|compare|num|大小|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|any|any|any|any|**EINVAL**|
|any|**Null**|any|!= 0|any|**EINVAL**|
|any|any|any|any|零|**EINVAL**|
|any|any|**Null**|一个|any|**EINVAL**|

## <a name="remarks"></a>备注

**_Lfind_s**函数对*数字*元素数组中的值*键*（每个*宽度*字节）执行线性搜索。 与**bsearch_s**不同， **_lfind_s**不需要对数组进行排序。 *Base*参数是指向要搜索的数组的基的指针。 *Compare*参数是指向用户提供的例程的指针，它比较两个数组元素，然后返回指定其关系的值。 **_lfind_s**在搜索过程中一次或多次调用*比较*例程，同时将*上下文*指针和指针传递到每个调用上的两个数组元素。 *比较*例程必须比较这些元素，然后返回非零值（表示元素不同）或0（表示元素相同）。

**_lfind_s**类似于 **_lfind** ，只不过将*上下文*指针添加到比较函数的自变量和函数的参数列表中。 如果搜索的数据结构是对象的一部分，并且*compare*函数需要访问该对象的成员，则*上下文*指针会很有用。 *Compare*函数可以将 void 指针转换为适当的对象类型并访问该对象的成员。 添加*上下文*参数会使 **_lfind_s**更为安全，因为可以使用其他上下文避免与使用静态变量关联的重入 bug，使数据可供*compare*函数使用。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
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

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
