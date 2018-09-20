---
title: A.20 barrier 指令的绑定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628920caa6a122230f42394cc757e3abdb1874cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381304"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   barrier 指令的绑定

指令的绑定规则调用**屏障**指令将绑定到最接近封闭`parallel`指令。 指令的绑定的详细信息，请参阅[部分 2.8](../../parallel/openmp/2-8-directive-binding.md)第 32 页上。

在下面的示例中，从调用*主要*到*sub2 来*兼容因为**屏障**(在*sub3*) 将绑定到并行区域在中*sub2 来*。 从调用*主要*到*sub1*兼容因为**屏障**将绑定到子例程中的并行区域*sub2 来*。  从调用*主要*到*sub3*兼容因为**屏障**不绑定到任何并行区域并将被忽略。 另请注意，**屏障**仅同步团队的封闭并行区域中的线程和中创建的不是所有线程*sub1*。

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```