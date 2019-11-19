---
title: 编译器警告（等级1） C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: 242c854339608c88d139c898d81d142c52f90134
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966315"
---
# <a name="compiler-warning-level-1-c4401"></a>编译器警告（等级1） C4401

"位域"：成员是位域

内联程序集代码尝试访问位域成员。 内联程序集无法访问位域成员，因此，在使用位域成员之前的最后一个装箱边界。

若要避免此警告，请在内联程序集代码中进行引用之前，将位域转换为适当的类型。 下面的示例生成 C4401：

```cpp
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```