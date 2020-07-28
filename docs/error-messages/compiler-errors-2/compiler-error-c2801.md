---
title: 编译器错误 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: cfb89c79534318ab1fbcaa06667d594bfe2f1157
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214589"
---
# <a name="compiler-error-c2801"></a>编译器错误 C2801

"operator operator" 必须是非静态成员

以下运算符只能重载为非静态成员：

- #A1`=`

- 类成员访问`->`

- 下标`[]`

- 函数调用`()`

可能的 C2801 原因：

- 重载运算符不是类、结构或联合成员。

- 已声明重载运算符 **`static`** 。

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
