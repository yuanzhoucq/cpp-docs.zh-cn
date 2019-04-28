---
title: qsort
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 8a770965a03e43227b99f122924c723691f79c61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358094"
---
# <a name="qsort"></a>qsort

执行快速排序。 此函数有一个更安全的版本；请参阅 [qsort_s](qsort-s.md)。

## <a name="syntax"></a>语法

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>参数

*base*<br/>
目标数组的开头。

*number*<br/>
元素中的数组大小。

*width*<br/>
元素大小（字节）。

*compare*<br/>
指向用户提供的例程的指针比较两个数组元素，并返回指定它们关系的值。

## <a name="remarks"></a>备注

**Qsort**函数可实现一种快速排序算法进行排序的数组*数量*，每个元素*宽度*字节。 自变量*基*是指向要进行排序的数组的基的指针。 **qsort**将使用已排序的元素覆盖此数组。

**qsort**调用*比较*例程的一个或多个排序，次，将指针传递给两个数组元素，在每次调用。

```C
compare( (void *) & elem1, (void *) & elem2 );
```

该例程将比较元素，并返回下列值之一。

|比较函数返回值|描述|
|-----------------------------------|-----------------|
|< 0|**elem1**小于**elem2**|
|0|**elem1**等效于**elem2**|
|> 0|**elem1**大于**elem2**|

数组按比较函数中定义的升序进行排序。 若要以降序对数组进行排序，请反转比较函数中的“大于”和“小于”的意义。

此函数验证其参数。 如果*比较*或*数量*是**NULL**，或者如果*基*是**NULL**和*数*不为零，或者如果*宽度*小于零，无效参数处理程序调用，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，该函数返回并**errno**设置为**EINVAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**qsort**|\<stdlib.h> 和 \<search.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
