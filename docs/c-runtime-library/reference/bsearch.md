---
title: bsearch
ms.date: 10/22/2019
api_name:
- bsearch
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 6b476cbdd5e9c072cae03ad1091a96e2d0b7422b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811097"
---
# <a name="bsearch"></a>bsearch

执行排序数组的二进制搜索。 此函数有一个更安全的版本；请参阅 [bsearch_s](bsearch-s.md)。

## <a name="syntax"></a>语法

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>参数

*密钥*\
指向要搜索的键的指针。

*base*\
指向搜索数据的基的指针。

*数字*\
元素数量。

*width*\
元素的宽度。

*比较*\
比较两个元素的回调函数。 第一个是指向用于搜索的键的指针，第二个参数是指向要与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

**bsearch**返回一个指针，该指针指向由*base*指向的数组中的*键*的匹配项。 如果未找到*键*，则该函数返回**NULL**。 如果数组不是以升序排序的，或包含具有相同键的重复记录，则不可预知结果。

## <a name="remarks"></a>备注

**Bsearch**函数对*数字*元素的已排序数组执行二进制搜索，其中每个大小均为大小的*宽度*字节。 *基值*是指向要搜索的数组的基的指针，而*键*是正在查找的值。 *Compare*参数是指向用户提供的例程的指针，它将所请求的密钥与数组元素进行比较。 它将返回以下值之一，用于指定其关系：

|*比较*例程返回的值|描述|
|-----------------------------------------|-----------------|
|\< 0|键小于数组元素。|
|0|键等于数组元素。|
|> 0|键大于数组元素。|

此函数验证其参数。 如果为*compare*、 *key*或*number*为**null**，或者*base*为**null**且*number*为非零，或者*width*为零，则函数将调用无效参数处理程序，如参数中所述。 [验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则将**errno**设置为 `EINVAL`，该函数将返回**NULL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> 和 \<search.h>|

有关其他兼容性信息，请参见 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序对具有 qsort 的字符串数组进行排序，然后使用 bsearch 查找单词“cat”。

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
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

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
