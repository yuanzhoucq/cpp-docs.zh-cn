---
title: 编译器警告（等级 4）C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: c752b5daea42eac7c7dd0e14581d9e781aac9c96
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988735"
---
# <a name="compiler-warning-level-4-c4938"></a>编译器警告（等级 4）C4938

“var”：浮点型 reduction 变量可能会导致在 /fp:strict 或 #pragma fenv_access 下出现不一致的结果

不应将 OpenMP 浮点型 reduction 变量与 [/fp: strict](../../build/reference/fp-specify-floating-point-behavior.md) 或 [fenv_access](../../preprocessor/fenv-access.md) 同时使用，因为求和计算的顺序不同。 因此，结果可能与不使用 /openmp 的结果不同。

下面的示例生成 C4938：

```cpp
// C4938.cpp
// compile with: /openmp /W4 /fp:strict /c
// #pragma fenv_access(on)
extern double *a;

double test(int first, int last) {
   double sum = 0.0;
   #pragma omp parallel for reduction(+: sum)   // C4938
   for (int i = first ; i <= last ; ++i)
      sum += a[i];
   return sum;
}
```

有显式并行化时，求和计算按如下方式进行：

```
sum = a[first] + a[first + 1] + ... + a[last];
```

无显式并行化时，求和计算按如下方式进行：

```
sum1 = a[first] + ... a[first + last / 2];
sum2 = a[(first + last / 2) + 1] + ... a[last];
sum = sum1 + sum2;
```
