---
title: OpenMP 子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378316"
---
# <a name="openmp-clauses"></a>OpenMP 子句

提供指向子句在 OpenMP API 中使用。

Visual c + + 支持以下 OpenMP 子句：

|子句|描述|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|允许线程访问主线程的值为[threadprivate](../../../parallel/openmp/reference/threadprivate.md)变量。|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|指定应在所有线程之间共享一个或多个变量。|
|[default](../../../parallel/openmp/reference/default-openmp.md)|并行区域中指定的未区分范围的变量的行为。|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|指定每个线程应具有它自己的实例的变量和变量应使用变量的值进行初始化，因为它在并行构造之前存在。|
|[if](../../../parallel/openmp/reference/if-openmp.md)|指定并行或序列中是否应执行一个循环。|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|指定变量在封闭上下文版本将设置为专用版本的任何线程执行的最后一次迭代 （for 循环构造） 或最后一个部分 （#pragma 节）。|
|[nowait](../../../parallel/openmp/reference/nowait.md)|重写屏障指令中隐式。|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|设置线程团队中的线程数。|
|[排序](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|在并行所需[有关](../../../parallel/openmp/reference/for-openmp.md)语句如果[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)指令是在循环中使用。|
|[private](../../../parallel/openmp/reference/private-openmp.md)|指定每个线程应具有其自己的变量的实例。|
|[reduction](../../../parallel/openmp/reference/reduction.md)|指定对每个线程都是私有的一个或多个变量来降低操作并行区域末尾的使用者。|
|[schedule](../../../parallel/openmp/reference/schedule.md)|适用于[为](../../../parallel/openmp/reference/for-openmp.md)指令。|
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|指定应在所有线程之间共享一个或多个变量。|

## <a name="see-also"></a>请参阅

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[指令](../../../parallel/openmp/reference/openmp-directives.md)