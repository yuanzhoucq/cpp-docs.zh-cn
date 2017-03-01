---
title: "_lsearch_s |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6f89899e5fe2c00cf17a7a18c9de2eac2ba8462f
ms.lasthandoff: 02/24/2017

---
# <a name="lsearchs"></a>_lsearch_s
对值执行线性搜索。 [_lsearch](../../c-runtime-library/reference/lsearch.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的对象。  
  
 `base`  
 指向要搜索的数组基的指针。  
  
 `num`  
 元素数量。  
  
 `size`  
 各个数组元素的大小（以字节为单位）。  
  
 `compare`  
 指向比较例程的指针。 第二个参数是指向要搜索的键的指针。 第三个参数是指向要与该键进行比较的数组元素的指针。  
  
 `context`  
 指向可在比较函数中访问的对象的指针。  
  
## <a name="return-value"></a>返回值  
 如果找到 `key`，则 `_lsearch_s` 返回指向 `base` 处的与 `key` 匹配的数组元素的指针。 如果未找到 `key`，则 `_lsearch_s` 返回指向数组末尾处的新添加项的指针。  
  
 如果传递给此函数的参数无效，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>错误条件  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|任何|任何|任何|任何|`EINVAL`|  
|任何|`NULL`|任何|!= 0|任何|`EINVAL`|  
|任何|任何|任何|any|零|`EINVAL`|  
|any|任何|`NULL`|一个|任何|`EINVAL`|  
  
## <a name="remarks"></a>备注  
 `_lsearch_s` 函数对 `num` 元素的数组中的值 `key` 执行线性搜索，每个元素为 `width` 字节。 与 `bsearch_s` 不同的是，`_lsearch_s` 不要求对数组进行排序。 如果未找到 `key`，则 `_lsearch_s` 将其添加到数组末尾并增加 `num`。  
  
 `compare` 函数是指向提供给用户的例程的指针，它比较两个数组元素，并返回指定其关系的值。 `compare` 函数还将指向上下文的指针作为第一个参数。 `_lsearch_s` 在搜索过程中调用 `compare` 一次或多次，将指针传递给每个调用上的两个数组元素。 `compare` 必须比较这些元素，然后返回非零值（表示元素不同）或 0（表示元素相同）。  
  
 如果搜索的数据结构是对象的一部分，且 `compare` 函数需要访问该对象的成员，则 `context` 指针可能有用。 例如，`compare` 函数中的代码可将 void 指针转换为适当的对象类型并访问该对象的成员。 添加 `context` 指针将使 `_lsearch_s` 更安全，因为其他上下文可用于避免重新进入 Bug 与使用静态变量以使数据对 `compare` 函数可用相关联。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_lsearch_s`|\<search.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [搜索和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)
