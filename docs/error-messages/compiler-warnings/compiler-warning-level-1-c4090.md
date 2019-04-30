---
title: 编译器警告 （等级 1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406465"
---
# <a name="compiler-warning-level-1-c4090"></a>编译器警告 （等级 1） C4090

operation： 不同 modifier 限定符

使用指定的修饰符，以防止它被修改而不被检测由编译器定义在操作中使用的变量。 无需修改即可编译表达式。

当指向的指针时，可以导致此警告**const**或`volatile`项分配给指针不能声明为指向**const**或`volatile`。

对于 C 程序将发出此警告。 在C++程序，则编译器会发出错误：[而产生的 C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

下面的示例生成 C4090:

```
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```