---
title: 编译器错误 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 4904c7009151748b4585060c816e0bd5c407be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225548"
---
# <a name="compiler-error-c2178"></a>编译器错误 C2178

"*identifier*" 不能用 "*说明符*" 说明符进行声明

**`mutable`** 在声明中使用了说明符，但此上下文中不允许使用说明符。

**`mutable`** 说明符仅可应用于类数据成员的名称，不能应用于声明或的名称， **`const`** 并且不能应用于 **`static`** 引用成员。

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
