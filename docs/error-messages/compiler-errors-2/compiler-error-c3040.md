---
title: 编译器错误 C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: b0bc4956cfc08ae50026827d78136a70b82d568e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349992"
---
# <a name="compiler-error-c3040"></a>编译器错误 C3040

“var”：“reduction”子句中的变量类型与 reduction 运算符“operator”不兼容

[reduction](../../parallel/openmp/reference/reduction.md) 子句中的变量不能与 reduction 运算符一起使用。

下面的示例生成 C3040：

```
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```