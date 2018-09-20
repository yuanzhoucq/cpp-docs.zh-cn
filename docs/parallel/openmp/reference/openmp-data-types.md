---
title: OpenMP 数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b41eaf7012c1d119071281f98177e4a4d841890b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410062"
---
# <a name="openmp-data-types"></a>OpenMP 数据类型

OpenMP API 中使用的数据类型到提供的链接。

OpenMP 标准的 Visual c + + 实现包括以下数据类型。

|数据类型|描述|
|---------------|-----------------|
|[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)|一个类型，持有锁、 锁是否可用，或如果线程拥有锁的状态。|
|[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)|包含有关某个锁的信息的以下部分之一的类型： 是否锁可用，并且线程标识拥有锁和嵌套的计数。|

## <a name="see-also"></a>请参阅

[库参考](../../../parallel/openmp/reference/openmp-library-reference.md)