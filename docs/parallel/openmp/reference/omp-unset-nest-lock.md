---
title: omp_unset_nest_lock |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03ea941e793f8c3a9f40e0495442deb71b2ffa93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402715"
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock

释放可嵌套锁。

## <a name="syntax"></a>语法

```
void omp_unset_nest_lock( 
   omp_nest_lock_t *lock 
);
```

### <a name="parameters"></a>参数

*lock*<br/>
类型的变量[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)与初始化[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)、 由线程拥有和函数中执行。

## <a name="remarks"></a>备注

有关详细信息，请参阅[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

## <a name="example"></a>示例

请参阅[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)有关的使用示例`omp_unset_nest_lock`。

## <a name="see-also"></a>请参阅

[函数](../../../parallel/openmp/reference/openmp-functions.md)