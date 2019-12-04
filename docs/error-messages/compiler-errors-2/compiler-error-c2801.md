---
title: 编译器错误 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760668"
---
# <a name="compiler-error-c2801"></a>编译器错误 C2801

"operator operator" 必须是非静态成员

以下运算符只能重载为非静态成员：

- 赋值 `=`

- 类成员访问 `->`

- 下标 `[]`

- 函数调用 `()`

可能的 C2801 原因：

- 重载运算符不是类、结构或联合成员。

- 重载运算符是 `static`声明的。

- 下面的示例生成 C2801：

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
