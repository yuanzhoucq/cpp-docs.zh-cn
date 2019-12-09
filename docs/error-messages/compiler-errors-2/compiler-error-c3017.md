---
title: 编译器错误 C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: af3f24a1a814fa79fa63b7e5bee204083006c9a2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749735"
---
# <a name="compiler-error-c3017"></a>编译器错误 C3017

OpenMP“for”语句中的终止测试格式不正确

必须完全或显式指定 OpenMP 语句中的 `for` 循环。

下面的示例生成 C3017：

```cpp
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```
