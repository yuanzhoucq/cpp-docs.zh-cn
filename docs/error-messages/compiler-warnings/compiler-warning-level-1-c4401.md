---
title: 编译器警告（等级 1）C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: c7e6cf8a52288d895b74481678dc91fee387a6a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455414"
---
# <a name="compiler-warning-level-1-c4401"></a>编译器警告（等级 1）C4401

位域： 成员是位域

内联程序集代码尝试访问位域成员。 内联程序集不能访问位域成员，因此使用位域成员之前的最后一个封装边界。

若要避免此警告，将位域转换为适当的类型进行内联程序集代码中引用之前。 下面的示例生成 C4401:

```
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