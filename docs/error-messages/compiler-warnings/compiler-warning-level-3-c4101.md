---
title: 编译器警告 （等级 3） C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: d1109a32e754a6055e5e1d90632ad85332d832f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402315"
---
# <a name="compiler-warning-level-3-c4101"></a>编译器警告 （等级 3） C4101

identifier： 未引用的局部变量

从不使用本地变量。 此警告会在明显这种情况中：

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

但是，此警告将在调用时也发生**静态**通过类的实例成员函数：

```
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

在此情况下，编译器所使用的有关的信息`si`访问**静态**函数，但类的实例时不需要调用**静态**函数; 因此该警告。 若要解决此警告，可以：

- 添加构造函数，编译器将在其中使用的实例`si`对的调用中`func`。

- 删除**静态**定义中的关键字`func`。

- 调用**静态**函数显式： `int y = S::func();`。