---
title: A.24 private 子句的示例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df2efc9fe111fa6e8d0b0507eceb20f07f48b02d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416235"
---
# <a name="a24---example-of-the-private-clause"></a>A.24   private 子句的示例

`private`子句 ([部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上) 的并行区域是仅在影响词法范围内的区域，而不适用于区域的动态范围中。  因此，在以下示例中，使用该变量的任何内`for`例程中的循环*f*的私有副本是指，while 中的使用情况例程*g*引用全局。

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```