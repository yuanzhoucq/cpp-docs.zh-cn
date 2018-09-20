---
title: omp_get_dynamic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2b5a285ef019cd1752b60065f7040d9a937ce38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389884"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic

返回一个值，该值指示是否后续并行区域中可用的线程数可以调整运行时。

## <a name="syntax"></a>语法

```
int omp_get_dynamic();
```

## <a name="return-value"></a>返回值

如果非零值，则启用动态调整线程。

## <a name="remarks"></a>备注

使用指定的线程的动态调整[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)并[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。

有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

## <a name="example"></a>示例

请参阅[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)有关的使用示例`omp_get_dynamic`。

## <a name="see-also"></a>请参阅

[函数](../../../parallel/openmp/reference/openmp-functions.md)