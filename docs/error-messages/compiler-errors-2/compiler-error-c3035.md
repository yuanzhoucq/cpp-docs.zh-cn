---
title: 编译器错误 C3035
ms.date: 11/04/2016
f1_keywords:
- C3035
helpviewer_keywords:
- C3035
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
ms.openlocfilehash: 0064d07d0e6d8adaa41d81272e315685dd32a74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755013"
---
# <a name="compiler-error-c3035"></a>编译器错误 C3035

OpenMP“ordered”指令必须使用“ordered”子句直接绑定到“for”或“parallel for”指令

ordered 子句的格式不正确。

下面的示例生成 C3035：

```cpp
// C3035.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   int n = 0, x, i;

   #pragma omp parallel private(n)
   {
      #pragma omp ordered   // C3035
      // Try the following line instead:
      // #pragma omp for ordered
       for (i = 0 ; i < 10 ; ++i)
         ;
   }
}
```
