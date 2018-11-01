---
title: 编译器警告 （等级 1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 0d947a0f6d777a5ed3191d6d232a604028be2003
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477449"
---
# <a name="compiler-warning-level-1-c4183"></a>编译器警告 （等级 1） C4183

identifier： 缺少返回类型;假定为返回 int 的成员函数

在类或结构中的成员函数的内联定义没有返回类型。 假定此成员函数的返回类型的默认`int`。

下面的示例生成 C4183:

```
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```