---
title: 编译器错误 C3003
ms.date: 11/04/2016
f1_keywords:
- C3003
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
ms.openlocfilehash: 6d15d8bde8855b8dcc4857492acdeb950731b503
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537541"
---
# <a name="compiler-error-c3003"></a>编译器错误 C3003

“directive”：在指令子句之后不允许使用 OpenMP 指令名称

OpenMP 指令名称不能位于 OpenMP 指令子句之后。

下面的示例生成 C3003：

```
// C3003.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x, y, z) for   // C3003
}
```