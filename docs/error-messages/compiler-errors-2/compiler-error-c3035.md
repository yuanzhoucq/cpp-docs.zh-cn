---
title: 编译器错误 C3035 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3035
dev_langs:
- C++
helpviewer_keywords:
- C3035
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e3be9974d299018af77bde0989b1bdc18889706
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081567"
---
# <a name="compiler-error-c3035"></a>编译器错误 C3035

OpenMP“ordered”指令必须使用“ordered”子句直接绑定到“for”或“parallel for”指令

ordered 子句的格式不正确。

下面的示例生成 C3035：

```
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