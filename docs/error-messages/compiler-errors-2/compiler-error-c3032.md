---
title: 编译器错误 C3032
ms.date: 11/04/2016
f1_keywords:
- C3032
helpviewer_keywords:
- C3032
ms.assetid: 6a92bd8e-319f-4a99-aef4-a9021f6f9928
ms.openlocfilehash: c9ea9d1baa0bab1141b1a0f3882df78f32208d0b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748302"
---
# <a name="compiler-error-c3032"></a>编译器错误 C3032

“var”: “clause”子句中的变量不能是不完整的“类型”类型

传递给某些子句的类型必须对编译器完全可见。

下面的示例生成 C3032:

```cpp
// C3032.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

struct Incomplete;
extern struct Incomplete inc;

int main() {
   int i = 9;
   #pragma omp parallel private(inc)   // C3032
      ;

   #pragma omp parallel private(i)     // OK
      ;

}
```
