---
title: 编译器警告（等级3） C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 0ac34fbaf4cbb54583394dff5b8645fe56b8b9cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199040"
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

但是，当通过类的实例调用**静态**成员函数时，也会出现此警告：

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

在这种情况下，编译器使用有关 `si` 的信息来访问**静态**函数，但不需要类的实例来调用**静态**函数;因此会出现警告。 若要解决此警告，可以执行以下操作：

- 添加一个构造函数，在此构造函数中，编译器将在调用 `func`时使用的实例 `si`。

- 从 `func`的定义中删除**static**关键字。

- 显式调用**静态**函数： `int y = S::func();`。
