---
title: 编译器错误 C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: 56ae2ddf35148fe263e406f48526cd68c4f91352
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748289"
---
# <a name="compiler-error-c3034"></a>编译器错误 C3034

OpenMP“directive1”指令不能直接嵌套在“directive2”指令中

一些指令不能嵌套。 若要修复此错误，你可以将这两个指令语句合并到一个指令的块中或可以构造连续指令。

以下示例生成 C3034：

```cpp
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```
