---
title: 编译器错误 C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744727"
---
# <a name="compiler-error-c2422"></a>编译器错误 C2422

"操作数" 中的非法段重写

内联程序集代码错误地在操作数上使用段重写运算符（冒号）。  可能的原因包括：

- 运算符前面的寄存器不是段寄存器。

- 运算符前面的寄存器不是操作数中唯一的段寄存器。

- 段 override 运算符出现在间接运算符（方括号）中。

- 段重写运算符后面的表达式不是即时操作数或内存操作数。

下面的示例生成 C2422：

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
