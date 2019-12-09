---
title: 编译器错误 C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 983788f041651fcd313c0707a4a7c64cc6e33c5a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755533"
---
# <a name="compiler-error-c2563"></a>编译器错误 C2563

形参表中不匹配

函数的形参列表（或指向某个函数的指针）与另一个函数（或指向成员函数的指针）的形参列表不匹配。 因此，无法对函数或指针赋值。

下面的示例生成 C2563：

```cpp
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
