---
title: 编译器警告（等级 1）C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: af091d1d35fff955afcc5af3da48b80416e79f36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485626"
---
# <a name="compiler-warning-level-1-c4731"></a>编译器警告（等级 1）C4731

指针： 框架指针寄存器注册被内联程序集代码修改

修改帧指针寄存器。 您必须保存和还原的寄存器在内联程序集块或帧变量 （局部变量或参数，具体取决于修改的寄存器），或你的代码可能无法正常工作。

下面的示例生成 C4731:

```
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

EBP 是帧指针 （不允许 FPO） 并对其进行修改。 当`p`晚引用，它引用相对于`EBP`。 但`EBP`已被覆盖的代码，所以程序将无法正常工作，甚至可能出现故障。