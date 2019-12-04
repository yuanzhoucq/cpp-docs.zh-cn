---
title: 编译器错误 C2882
ms.date: 11/04/2016
f1_keywords:
- C2882
helpviewer_keywords:
- C2882
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
ms.openlocfilehash: a1c6f20ae33a545ae2e6bd7b373ecf2444e0d1d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736160"
---
# <a name="compiler-error-c2882"></a>编译器错误 C2882

"name"：在表达式中非法使用命名空间标识符

您尝试在表达式中使用命名空间的名称。

下面的示例生成 C2882：

```cpp
// C2882.cpp
// compile with: /c
namespace A {
   int k;
}

int i = A;   // C2882, can't assign A to i
```
