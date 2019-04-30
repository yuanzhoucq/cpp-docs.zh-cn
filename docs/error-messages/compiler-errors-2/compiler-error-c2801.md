---
title: 编译器错误 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 44f7988f9fedb882972b2823f2fe70d9512d4e87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408675"
---
# <a name="compiler-error-c2801"></a>编译器错误 C2801

operator operator 必须为非静态成员

可以仅为非静态成员重载以下运算符：

- 赋值 `=`

- 类成员访问 `->`

- 下标 `[]`

- 函数调用 `()`

C2801 的可能原因：

- 重载的运算符不是类、 结构或联合成员。

- 重载的运算符被声明`static`。

- 下面的示例生成 C2801:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```