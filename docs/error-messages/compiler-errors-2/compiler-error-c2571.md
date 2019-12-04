---
title: 编译器错误 C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 7bd87f0732e1a632b8c86cc57fab1a0f104b2c77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755494"
---
# <a name="compiler-error-c2571"></a>编译器错误 C2571

"function"：虚函数不能在联合 "union" 中

联合是使用虚函数声明的。 只能在类或结构中声明虚函数。  可能的解决方法：

1. 将联合更改为类或结构。

1. 使函数不是虚拟的。

下面的示例生成 C2571：

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
