---
title: 编译器错误 C3020 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3020
dev_langs:
- C++
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7f86d116c1a830db54490f3e5231d837d4246c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060637"
---
# <a name="compiler-error-c3020"></a>编译器错误 C3020

var: OpenMP for 循环索引变量不能在循环体中修改

OpenMP`for`循环不能修改的正文中的索引 （循环计数器）`for`循环。

下面的示例生成 C3020:

```
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

与声明的变量[lastprivate](../../parallel/openmp/reference/lastprivate.md)不能用作在并行化循环内的索引。

下面的示例将为第二个 lastprivate 提供 C3020，因为该 lastprivate 会触发写入中最外面的 idx_a for 循环。 第一个 lastprivate 不会给出错误消息，因为该 lastprivate 会触发写入之外最外面的 idx_a for 循环 （从技术上讲，在最后一次迭代最后）。 下面的示例生成 C3020。

```
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

```
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