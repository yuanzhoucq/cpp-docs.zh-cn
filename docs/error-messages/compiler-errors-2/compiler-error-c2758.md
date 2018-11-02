---
title: 编译器错误 C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c3a86b8b8c7f122929a52221d4f01a17c50395be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618021"
---
# <a name="compiler-error-c2758"></a>编译器错误 C2758

“member”：必须初始化引用类型的成员

如果构造函数未初始化初始值设定项列表中引用类型的成员，则会导致编译器错误 C2758。 编译器将该成员保留为未定义状态。 如果已在构造函数的初始化列表中声明引用成员变量或为其赋值，则必须对其进行初始化。

下面的示例生成 C2758：

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```