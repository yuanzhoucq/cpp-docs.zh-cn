---
title: OpenMP 数据类型
ms.date: 10/23/2018
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
ms.openlocfilehash: bacb48194015f8fd6c80a9868af06702deceab6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533765"
---
# <a name="openmp-data-types"></a>OpenMP 数据类型

OpenMP API 中使用的数据类型到提供的链接。

OpenMP 标准的 Visual c + + 实现包括以下数据类型。

|数据类型|描述|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|一个类型，持有锁、 锁是否可用，或如果线程拥有锁的状态。|
|[omp_nest_lock_t](#omp-nest-lock-t)|包含有关某个锁的信息的以下部分之一的类型： 是否锁可用，并且线程标识拥有锁和嵌套的计数。|

## <a name="omp-lock-t"></a>omp_lock_t

一个类型，持有锁、 锁是否可用，或如果线程拥有锁的状态。

以下函数使用`omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

有关详细信息，请参阅[3.2 锁函数](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_lock](openmp-functions.md#omp-init-lock)有关的使用示例`omp_lock_t`。

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

保留以下几部分有关某个锁的信息的类型： 是否锁可用，并且线程标识拥有锁和嵌套的计数。

以下函数使用`omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

有关详细信息，请参阅[3.2 锁函数](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>示例

请参阅[omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)有关的使用示例`omp_nest_lock_t`。
