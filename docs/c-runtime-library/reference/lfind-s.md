---
title: _lfind_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 08c04d9d1ca69998d54304c96468298013907179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286422"
---
# <a name="lfinds"></a>_lfind_s

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

*key*<br/>
要搜索的对象。

*base*<br/>
指向搜索数据的基项的指针。

*number*<br/>
数组元素的数目。

*size*<br/>
以字节为单位的数组元素的大小。

*compare*<br/>
指向比较例程的指针。 第一个参数是*上下文*指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。

*context*<br/>
指向可能在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

如果找到该键，则 **_lfind_s**处的数组的元素返回指向*基*相匹配*密钥*。 如果未找到该键， **_lfind_s**返回**NULL**。

如果传递到此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回**NULL**。

### <a name="error-conditions"></a>错误条件

|密钥|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|零|**EINVAL**|
|任何|任何|**NULL**|一个|任何|**EINVAL**|

## <a name="remarks"></a>备注

**_Lfind_s**函数执行值的线性搜索*密钥*数组中的*数*，每个元素*宽度*字节。 与不同**bsearch_s**， **_lfind_s**不需要要进行排序的数组。 *基*参数是指向待搜索数组基的指针。 *比较*参数是指向用户提供的比较两个数组元素，然后返回一个值，指定其关系的例程的指针。 **_lfind_s**调用*比较*例程的一个或多个时间搜索，并传递过程*上下文*指针和指向每个调用上的两个数组元素的指针。 *比较*例程必须比较这些元素，然后返回非零值 （表示元素是不同的） 或 0 （表示元素相同）。

**_lfind_s**类似于 **_lfind**除了添加*上下文*指向比较函数的参数和函数的参数列表。 *上下文*指针可能有用，如果搜索的数据结构是对象的一部分并*比较*函数需要访问对象的成员。 *比较*函数可将 void 指针转换该对象的适当的对象类型并访问成员。 添加了*上下文*参数将使得 **_lfind_s**更加安全，因为其他上下文可用于避免重新进入 bug 与使用静态变量以使数据可供关联*比较*函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
