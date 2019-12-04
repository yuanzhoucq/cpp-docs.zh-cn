---
title: 编译器错误 C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 4347e5ee0e61ada700082b4954b616ce894e57b9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761385"
---
# <a name="compiler-error-c3042"></a>编译器错误 C3042

“copyprivate”和“nowait”子句不能同时出现在 OpenMP“directive”指令中

[Copyprivate](../../parallel/openmp/reference/copyprivate.md) 和 [nowait](../../parallel/openmp/reference/nowait.md) 子句在指定的指令上彼此排斥。 若要修复此错误，请删除 `copyprivate` 或 `nowait` 子句之一或两者一起删除。

以下示例生成 C3042：

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
