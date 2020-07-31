---
title: 编译器错误 C3015
ms.date: 11/04/2016
f1_keywords:
- C3015
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
ms.openlocfilehash: db87b035d76d4e3d2cf3f05c30ebddf0b6d22d5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232100"
---
# <a name="compiler-error-c3015"></a>编译器错误 C3015

OpenMP“for”语句中的初始化格式不正确

**`for`** OpenMP 语句中的循环必须完全明确地指定。

以下示例生成 C3015：

```cpp
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```
