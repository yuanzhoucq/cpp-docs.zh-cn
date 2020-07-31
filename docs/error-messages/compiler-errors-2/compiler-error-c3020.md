---
title: 编译器错误 C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: 89b28ae396322859596b99ba56a28375e9c9d6d5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232022"
---
# <a name="compiler-error-c3020"></a>编译器错误 C3020

"var"： OpenMP "for" 循环的索引变量不能在循环体中修改

OpenMP **`for`** 循环不能修改循环体中的索引（loop 计数器） **`for`** 。

下面的示例生成 C3020：

```cpp
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

使用[lastprivate](../../parallel/openmp/reference/lastprivate.md)声明的变量不能用作并行化循环内的索引。

下面的示例将为第二个 lastprivate 提供 C3020，因为 lastprivate 将在最外面的 for 循环内触发写入 idx_a。 第一个 lastprivate 不会给出错误，因为 lastprivate 触发了写入 idx_a 超出最外层 for 循环（从技术上讲到最后一次迭代的最末尾）。 下面的示例生成 C3020。

```cpp
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

以下示例演示了可能的解决方法：

```cpp
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```
