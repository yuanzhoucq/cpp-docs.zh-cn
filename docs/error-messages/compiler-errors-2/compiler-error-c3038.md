---
title: 编译器错误 C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 26fee4f5d636ac56ae01499f6b600d38f56bbe46
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754961"
---
# <a name="compiler-error-c3038"></a>编译器错误 C3038

“var”：“private”子句中的变量不能是封闭上下文中的 reduction 变量

并行指令的 [reduction](../../parallel/openmp/reference/reduction.md) 子句中出现的变量不能在 [private](../../parallel/openmp/reference/private-openmp.md) 子句中指定，后者位于绑定到并行构造的工作共享指令上。

下面的示例生成 C3038：

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
