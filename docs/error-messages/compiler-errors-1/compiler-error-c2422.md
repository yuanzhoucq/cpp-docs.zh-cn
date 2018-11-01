---
title: 编译器错误 C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509130"
---
# <a name="compiler-error-c2422"></a>编译器错误 C2422

操作数中的非法段重写

内联程序集代码错误地使用操作数的段重写运算符 （冒号）。  可能的原因包括：

- 运算符前面的寄存器不段寄存器。

- 运算符前面的寄存器不是操作数中的唯一段寄存器。

- 段重写运算符将显示在间接寻址运算符 （括号）。

- 段重写运算符后的表达式不是即时操作数或内存操作数。

下面的示例生成 C2422:

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```