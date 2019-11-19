---
title: 编译器警告（等级1） C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: b2591756dfaa8887affbe4e470f1c98738b6b680
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052428"
---
# <a name="compiler-warning-level-1-c4731"></a>编译器警告（等级1） C4731

"指针"：框架指针寄存器 "register" 由内联程序集代码修改

修改了帧指针寄存器。 你必须在内联程序集块或框架变量（本地或参数，具体取决于修改的寄存器）中保存和还原寄存器，否则你的代码可能无法正常工作。

下面的示例生成 C4731：

```cpp
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP 是帧指针（不允许有 FPO），正在修改它。 稍后引用 `p` 时，相对于 `EBP`引用它。 但 `EBP` 已被代码覆盖，所以程序将无法正常工作，甚至可能出现故障。