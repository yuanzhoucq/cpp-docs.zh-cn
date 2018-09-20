---
title: omp_set_num_threads |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae9dbe52dba47208844b73175f20edcc591a3ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444939"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads

在后续的并行区域设置的线程数，除非被重写[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。

## <a name="syntax"></a>语法

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>参数

*num_threads*<br/>
并行区域中的线程数。

## <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.1 omp_set_num_threads 函数](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。

## <a name="example"></a>示例

请参阅[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)有关的使用示例`omp_set_num_threads`。

## <a name="see-also"></a>请参阅

[函数](../../../parallel/openmp/reference/openmp-functions.md)