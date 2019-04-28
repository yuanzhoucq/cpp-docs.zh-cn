---
title: _lsearch
ms.date: 11/04/2016
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
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285651"
---
# <a name="lsearch"></a>_lsearch

对值执行线性搜索；如果未找到，则添加到列表的末尾。 提供此函数的一个更安全的版本；请参阅 [_lsearch_s](lsearch-s.md)。

## <a name="syntax"></a>语法

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>参数

*key*<br/>
要搜索的对象。

*base*<br/>
指向要搜索的数组基的指针。

*number*<br/>
元素数量。

*width*<br/>
各个数组元素的宽度。

*compare*<br/>
指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

如果找到该键，则 **_lsearch**处的数组的元素返回指向*基*相匹配*密钥*。 如果未找到该键， **_lsearch**返回指向数组末尾处的新添加项的指针。

## <a name="remarks"></a>备注

**_Lsearch**函数执行值的线性搜索*密钥*数组中的*数*，每个元素*宽度*字节。 与不同**bsearch**， **_lsearch**不需要要进行排序的数组。 如果*键*未找到，则 **_lsearch**将其添加到末尾数组并增加*数*。

*比较*参数是指向用户提供的例程，它比较两个数组元素并返回一个值，指定其关系。 **_lsearch**调用*比较*期间搜索，将指针传递给两个数组元素，在每次调用例程的一个或多个时间。 *比较*必须比较这些元素，返回非零值 （表示元素不同） 或 0 （表示元素相同）。

此函数验证其参数。 如果*比较*，*密钥*或*数*是**NULL**，或者如果*基*是**NULL**并*数*不为零，或者如果*宽度*小于零，无效参数处理程序调用，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回**NULL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
