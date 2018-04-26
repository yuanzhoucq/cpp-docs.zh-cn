---
title: _lsearch_s |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _lsearch_s
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
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21d2aface59c4c2fd4247d299af26c63cdf46d45
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="lsearchs"></a>_lsearch_s

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

*数*<br/>
元素数量。

*size*<br/>
各个数组元素的大小（以字节为单位）。

*compare*<br/>
指向比较例程的指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。

*context*<br/>
指向可能在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

如果*密钥*找到，则 **_lsearch_s**将指针返回到在数组的元素*基*匹配*密钥*。 如果*密钥*未找到， **_lsearch_s**将指针返回到数组末尾处新增的项。

如果传递到此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，然后**errno**设置为**EINVAL**和该函数将返回**NULL**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*key*|*base*|*compare*|*数*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|零|**EINVAL**|
|任何|任何|**NULL**|一个|任何|**EINVAL**|

## <a name="remarks"></a>备注

**_Lsearch_s**函数执行值的线性搜索*密钥*数组中的*数*元素，每个*宽度*字节。 与不同**bsearch_s**， **_lsearch_s**不需要要进行排序的数组。 如果*密钥*找不到，然后 **_lsearch_s**将其添加到的数组和增量的末尾*数*。

*比较*函数是指向用户提供比较两个数组元素并返回一个值，指定其关系的例程的指针。 *比较*函数还采用指向作为第一个参数的上下文的指针。 **_lsearch_s**调用*比较*搜索，将指针传递给两个数组元素，在每次调用的一个或多个期间。 *比较*必须比较元素，然后返回任一非零 （这意味着元素不同） 或 0 （这意味着元素相同的）。

*上下文*指针会很有用的搜索的数据结构是对象的一部分和*比较*函数需要访问对象的成员。 例如，代码中*比较*函数可以将 void 指针转换该对象的合适的对象类型和访问成员。 添加*上下文*指针移至 **_lsearch_s**更为安全，因为其他上下文可用于避免重新进入 bug 与使用静态变量以使数据可供关联*比较*函数。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
