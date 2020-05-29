---
title: 编译器警告（等级1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 551309757f5e76e230d0a275da94ac94ec30fb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163918"
---
# <a name="compiler-warning-level-1-c4090"></a>编译器警告（等级1） C4090

"operation"：不同的 "修饰符" 限定符

操作中使用的变量是使用指定修饰符定义的，该修饰符可防止在编译器未检测到它的情况下对其进行修改。 不修改即可编译表达式。

如果将指向**const**或 `volatile` 项的指针分配给未声明为指向**const**或 `volatile`的指针，则可能会导致此警告。

对于 C 程序，将发出此警告。 在C++程序中，编译器会发出错误： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

下面的示例生成 C4090：

```c
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
