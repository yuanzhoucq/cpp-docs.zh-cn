---
title: 编译器警告（等级1） C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 182f9ff061fd2a8ebe5ea0046545412fca5f646a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965590"
---
# <a name="compiler-warning-level-1-c4405"></a>编译器警告（等级1） C4405

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