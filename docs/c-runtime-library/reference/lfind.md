---
title: _lfind
ms.date: 11/04/2016
api_name:
- _lfind
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: ec59340433b92334effa8004720e4f0756085670
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442916"
---
# <a name="_lfind"></a>_lfind

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

*数字*<br/>
数组元素的数目。

*width*<br/>
数组元素的宽度。

*compare*<br/>
指向比较例程的指针。 第一个参数是指向要搜索的键的指针。 第二个参数是指向要与该键进行比较的数组元素的指针。

## <a name="return-value"></a>返回值

如果找到该密钥， **_lfind**将返回一个指针，该指针指向匹配*键*的*基*中的数组元素。 如果找不到该密钥， **_lfind**将返回**NULL**。

## <a name="remarks"></a>备注

**_Lfind**函数对*数字*元素数组中的值*键*（每个*宽度*字节）执行线性搜索。 与**bsearch**不同， **_lfind**不需要对数组进行排序。 *Base*参数是指向要搜索的数组的基的指针。 *Compare*参数是指向用户提供的例程的指针，它比较两个数组元素，然后返回指定其关系的值。 **_lfind**在搜索过程中一次或多次调用*比较*例程，同时将指针传递到每个调用上的两个数组元素。 *比较*例程必须比较这些元素，然后返回非零值（表示元素不同）或0（表示元素相同）。

此函数验证其参数。 如果为*compare*、 *key*或*number*为**null**，或者*base*为**null**且*number*为非零，或者*width*小于零，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lfind**|\<search.h>|

有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
