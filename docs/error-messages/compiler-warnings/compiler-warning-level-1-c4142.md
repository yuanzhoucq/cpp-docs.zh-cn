---
title: 编译器警告 （等级 1） C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302275"
---
# <a name="compiler-warning-level-1-c4142"></a>编译器警告 （等级 1） C4142

类型的良性重定义

一种类型是对生成的代码没有影响的方式重新定义。

通过检查以下可能的原因进行修复：

- 在派生类的成员函数具有不同的返回类型从相应的成员函数的类的基类。

- 使用定义的类型`typedef`命令已重新定义使用不同的语法。

下面的示例生成 C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```