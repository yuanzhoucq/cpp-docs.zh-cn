---
title: 编译器警告（等级 1）C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: e85bdc995fe16f91e2e9c734dacc65ca0b7b622d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654905"
---
# <a name="compiler-warning-level-1-c4405"></a>编译器警告（等级 1）C4405

identifier： 标识符是保留的字

内联程序集的保留的字用作变量名称。 这可能会导致不可预知的结果。 若要解决此警告，避免使用内联程序集的保留字命名变量。 下面的示例生成 C4405:

```
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```