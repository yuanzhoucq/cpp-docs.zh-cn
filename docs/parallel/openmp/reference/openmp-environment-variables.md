---
title: OpenMP 环境变量 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b61535fd07066c4a1ee24658fdfe81047efc90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446564"
---
# <a name="openmp-environment-variables"></a>OpenMP 环境变量

提供指向 OpenMP API 中使用的环境变量。

OpenMP 标准的 Visual c + + 实现包括以下环境变量。 在程序启动时读取这些环境变量和它们的值对的修改将忽略在运行时 (例如，使用[_putenv、 _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

|环境变量|描述|
|--------------------------|-----------------|
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|指定 OpenMP 运行时是否可以调整并行区域中的线程数。|
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|指定是否已启用嵌套的并行度，除非启用或禁用与嵌套并行度`omp_set_nested`。|
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|并行区域中设置的最大线程数，除非被重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](../../../parallel/openmp/reference/num-threads.md)。|
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|修改的行为[计划](../../../parallel/openmp/reference/schedule.md)子句时`schedule(runtime)`中指定`for`或`parallel for`指令。|

## <a name="see-also"></a>请参阅

[库参考](../../../parallel/openmp/reference/openmp-library-reference.md)