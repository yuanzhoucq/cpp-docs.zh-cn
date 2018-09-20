---
title: OpenMP 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389442"
---
# <a name="openmp-directives"></a>OpenMP 指令

提供指向 OpenMP API 中使用的指令。

Visual c + + 支持以下 OpenMP 指令：

|指令|描述|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|指定将以原子方式更新的内存位置。|
|[barrier](../../../parallel/openmp/reference/barrier.md)|同步团队; 中的所有线程所有线程在屏障，都暂停，直到所有线程都执行屏障。|
|[critical](../../../parallel/openmp/reference/critical.md)|指定代码仅执行一个线程上一次。|
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定的所有线程都都共享的所有对象的内存的相同视图。|
|[for](../../../parallel/openmp/reference/for-openmp.md)|导致中完成的工作有关要在线程之间划分的并行区域内的循环。|
|[master](../../../parallel/openmp/reference/master.md)|指定仅 master threadshould 执行程序的部分。|
|[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定应如顺序循环执行循环并行化该代码。|
|[parallel](../../../parallel/openmp/reference/parallel.md)|定义并行区域，这是由多个线程并行执行的代码。|
|[部分](../../../parallel/openmp/reference/sections-openmp.md)|标识代码段来分担所有线程。|
|[single](../../../parallel/openmp/reference/single.md)|可以指定一段代码应在单个线程，不一定是主线程上执行。|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定一个变量是线程私有的。|

## <a name="see-also"></a>请参阅

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[子句](../../../parallel/openmp/reference/openmp-clauses.md)