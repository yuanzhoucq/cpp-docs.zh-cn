---
title: 编译器警告（等级3） C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: f9d3875fdc17def1e7d3bcb72149c5faf90f656a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220049"
---
# <a name="compiler-warning-level-3-c4101"></a>编译器警告（等级3） C4101

"identifier"：未引用的局部变量

从未使用过局部变量。 在这种情况下，将出现此警告：

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

但是，当 **`static`** 通过类的实例调用成员函数时，也会出现此警告：

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

在这种情况下，编译器使用有关 `si` 的信息来访问 **`static`** 函数，但不需要类的实例来调用 **`static`** 函数; 因此会出现警告。 若要解决此警告，可以执行以下操作：

- 添加一个构造函数，在此构造函数中，编译器将在调用时使用的实例 `si` `func` 。

- **`static`** 从的定义中删除关键字 `func` 。

- 显式调用 **`static`** 函数： `int y = S::func();` 。
