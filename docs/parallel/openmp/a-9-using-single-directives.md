---
title: A.9 使用 single 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3a201450d54355aa96f0ea712ad9fa0f70f63f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448085"
---
# <a name="a9---using-single-directives"></a>A.9   使用 single 指令

下面的示例演示`single`指令 ([部分 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) 15 页上)。 在示例中，只有一个线程 (通常遇到的第一个线程`single`指令) 打印进度消息。 用户必须对哪个线程将执行不进行任何假设`single`部分。 所有其他线程将跳过`single`部分，并在末尾的屏障停止`single`构造。 如果其他线程会继续运行而无需等待执行的线程`single`部分中，`nowait`子句可以指定在`single`指令。

```
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```