---
title: _lfind | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f60ea8dd05f9dffd6778c001e3f150f95744ae2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="lfind"></a>_lfind

用于针对指定的键执行线性搜索。 此函数有一个更安全的版本；请参阅 [_lfind_s](lfind-s.md)。

## <a name="syntax"></a>语法

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>参数

*key*<br/>
要搜索的对象。

*base*<br/>
指向搜索数据的基项的指针。

*数*<br/>
数组元素的数目。

*width*<br/>
数组元素的宽度。

*compare*<br/>
指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

如果找到该键， **_lfind**将指针返回到在数组的元素*基*匹配*密钥*。 如果未找到键， **_lfind**返回**NULL**。

## <a name="remarks"></a>备注

**_Lfind**函数执行值的线性搜索*密钥*数组中的*数*元素，每个*宽度*字节。 与不同**bsearch**， **_lfind**不需要要进行排序的数组。 *基*自变量是指向要搜索的数组的基类。 *比较*自变量是指向比较两个数组元素，然后返回一个值，指定其关系的用户提供例程。 **_lfind**调用*比较*搜索，将指针传递给两个数组元素，在每次调用例程的一个或多个期间。 *比较*例程必须比较元素，然后返回非零 （这意味着元素不同） 或 0 （这意味着元素相同的）。

此函数验证其参数。 如果*比较*，*密钥*或*数*是**NULL**，或者如果*基*为 NULL 和 **数*不为零，或者如果*宽度*小于零，无效参数处理程序调用时中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回**NULL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lfind**|\<search.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
