---
title: A.30   重新私有化的使用
ms.date: 11/04/2016
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
ms.openlocfilehash: dc1d142a282fe6bb55c9cc512e6a6e8155b286e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437318"
---
# <a name="a30---use-of-reprivatization"></a>A.30   重新私有化的使用

下面的示例演示如何重新私有化的变量。 可以标记为私有变量`private`再次在嵌套指令中。 它们无需封闭并行区域中的共享。

```
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```