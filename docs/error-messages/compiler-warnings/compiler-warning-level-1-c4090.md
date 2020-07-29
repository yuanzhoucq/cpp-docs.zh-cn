---
title: 编译器警告（等级1） C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: c4cb71355b4f3dca66c56ed4b89012ca9b9e646d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197041"
---
# <a name="compiler-warning-level-1-c4090"></a>编译器警告（等级1） C4090

"operation"：不同的 "修饰符" 限定符

操作中使用的变量是使用指定修饰符定义的，该修饰符可防止在编译器未检测到它的情况下对其进行修改。 不修改即可编译表达式。

如果将指向 **`const`** 或项的指针 **`volatile`** 分配给未声明为指向或的指针，则可能会导致此 **`const`** 警告 **`volatile`** 。

对于 C 程序，将发出此警告。 在 c + + 程序中，编译器会发出错误： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。

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
