---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341654"
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

*关键*<br/>
要搜索的对象。

*base*<br/>
指向要搜索的数组基的指针。

*number*<br/>
元素数量。

*大小*<br/>
各个数组元素的大小（以字节为单位）。

*比较*<br/>
指向比较例程的指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。

*上下文*<br/>
指向可在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

如果找到*键***，_lsearch_s**返回指向*基上*与*键*匹配的数组元素的指针。 如果未找到*键***，_lsearch_s**在数组末尾返回指向新添加的项的指针。

如果将无效参数传递给函数，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL，** 函数返回**NULL**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*关键*|*base*|*比较*|*number*|*大小*|**Errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**空**|any|any|any|any|**埃因瓦尔**|
|any|**空**|any|!= 0|any|**埃因瓦尔**|
|any|any|any|any|零|**埃因瓦尔**|
|any|any|**空**|一个|any|**埃因瓦尔**|

## <a name="remarks"></a>备注

**_lsearch_s**函数对*数字*元素数组中的值*键*执行线性搜索，每个数组都是*宽度*字节。 与**bsearch_s**不同 **，_lsearch_s**不需要对数组进行排序。 如果未找到*键*，则 **_lsearch_s**将其添加到数组的末尾并递增*编号*。

*比较*函数是指向用户提供的例程的指针，该例程比较两个数组元素并返回指定其关系的值。 *比较*函数还将指向上下文的指针作为第一个参数。 **_lsearch_s**调用在搜索期间*比较*一次或多次，将指针传递到每个调用上的两个数组元素。 *比较*必须比较元素，然后返回非零（表示元素不同）或 0（表示元素相同）。

如果搜索的数据结构是对象的一部分，并且*比较*函数需要访问对象的成员，则*上下文*指针非常有用。 例如，*比较*函数中的代码可以将 void 指针转换为相应的对象类型并访问该对象的成员。 添加*上下文*指针使 **_lsearch_s更安全，** 因为可以使用其他上下文来避免与使用静态变量使数据可用于*比较*函数相关的重入错误。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
