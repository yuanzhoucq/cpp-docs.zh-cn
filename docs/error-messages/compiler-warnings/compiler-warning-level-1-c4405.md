---
title: 编译器警告（等级 1）C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 7ec06e80ac8f61802258a62594029b15a55ebe42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162564"
---
# <a name="compiler-warning-level-1-c4405"></a>编译器警告（等级 1）C4405

"identifier"：标识符是保留字

为内联程序集保留的字用作变量名。 这可能会导致不可预知的结果。 若要修复此警告，请避免用为内联程序集保留的字命名变量。 下面的示例生成 C4405：

```cpp
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
