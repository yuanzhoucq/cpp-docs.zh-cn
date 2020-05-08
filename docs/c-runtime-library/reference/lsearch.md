---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 73bc82ed57692dee348448d2b523961324203ca9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911335"
---
# <a name="_lsearch"></a>_lsearch

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

*键*<br/>
要搜索的对象。

*base*<br/>
指向要搜索的数组基的指针。

*数字*<br/>
元素数量。

width <br/>
各个数组元素的宽度。

*并排*<br/>
指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

如果找到该密钥， **_lsearch**将返回一个指针，该指针指向匹配*键*的*基*中的数组元素。 如果未找到该键，则 **_lsearch**返回指向数组末尾的新添加项的指针。

## <a name="remarks"></a>备注

**_Lsearch**函数对*数字*元素数组中的值*键*（每个*宽度*字节）执行线性搜索。 与**bsearch**不同， **_lsearch**不需要对数组进行排序。 如果找不到*键*， **_lsearch**会将其添加到数组的末尾并递增*数字*。

*Compare*参数是指向用户提供的例程的指针，它比较两个数组元素，并返回指定其关系的值。 **_lsearch**在搜索过程中一次或多次调用*比较*例程，同时将指针传递到每个调用上的两个数组元素。 *compare*必须比较元素并返回非零值（表示元素不同）或0（表示元素相同）。

此函数验证其参数。 如果为*compare*、 *key*或*number*为**null**，或者*base*为**null**且*number*为非零，或者*width*小于零，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
