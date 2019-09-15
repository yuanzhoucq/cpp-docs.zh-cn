---
title: _lsearch_s
ms.date: 11/04/2016
api_name:
- _lsearch_s
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
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: 1c3c0ac41a4805acb558c75fb5ff4cbc0e3aa838
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953004"
---
# <a name="_lsearch_s"></a>_lsearch_s

对值执行线性搜索。 [_lsearch](lsearch.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
void *_lsearch_s(
   const void *key,
   void *base,
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
指向要搜索的数组基的指针。

*number*<br/>
元素数量。

*size*<br/>
各个数组元素的大小（以字节为单位）。

*compare*<br/>
指向比较例程的指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。

*context*<br/>
指向可能在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

如果找到了*键*，则 **_lsearch_s**将返回一个指针，该指针指向匹配*键*的*基*中的数组元素。 如果未找到*键*，则 **_lsearch_s**将返回指向数组末尾的新添加项的指针。

如果传递到此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**NULL**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*key*|*base*|*compare*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|零|**EINVAL**|
|任何|任何|**NULL**|一个|任何|**EINVAL**|

## <a name="remarks"></a>备注

**_Lsearch_s**函数对*数字*元素数组中的值*键*执行线性搜索，其中每个*宽度*字节。 与**bsearch_s**不同， **_lsearch_s**不需要对数组进行排序。 如果未找到*键*，则 **_lsearch_s**会将其添加到数组的末尾并递增*数字*。

*Compare*函数是一个指向用户提供的例程的指针，它比较两个数组元素，并返回指定其关系的值。 *Compare*函数还将指向上下文的指针作为第一个参数。 **_lsearch_s**调用在搜索过程中*比较*一次或多次，将指针传递给每个调用上的两个数组元素。 *compare*必须比较这些元素，然后返回非零值（表示元素不同）或0（表示元素相同）。

如果搜索的数据结构是对象的一部分，并且*compare*函数需要访问该对象的成员，则*上下文*指针会很有用。 例如， *compare*函数中的代码可以将 void 指针转换为适当的对象类型并访问该对象的成员。 添加*上下文*指针会使 **_lsearch_s**更安全，因为其他上下文可用于避免与使用静态变量关联的重入 bug，以使数据可供*compare*函数使用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
