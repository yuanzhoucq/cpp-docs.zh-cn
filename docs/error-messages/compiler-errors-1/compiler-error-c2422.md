---
title: 编译器错误 C2422 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17421f2d4a7823c0e2fbb34a54a7c562223c798c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047026"
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