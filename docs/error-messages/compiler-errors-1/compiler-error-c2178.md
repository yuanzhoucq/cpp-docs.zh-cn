---
title: 编译器错误 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737187"
---
# <a name="compiler-error-c2178"></a>编译器错误 C2178

"*identifier*" 不能用 "*说明符*" 说明符进行声明

在声明中使用了 `mutable` 说明符，但此上下文中不允许使用说明符。

`mutable` 说明符仅可应用于类数据成员的名称，不能应用于 `const` 或 `static`声明的名称，并且不能应用于引用成员。

## <a name="example"></a>示例

下面的示例演示了如何进行 C2178，以及如何修复该问题。

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
