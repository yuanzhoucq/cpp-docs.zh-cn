---
title: 编译器错误 C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622555"
---
# <a name="compiler-error-c2178"></a>编译器错误 C2178

'*标识符*不能使用声明'*说明符*说明符

一个`mutable`在声明中，未使用说明符，但在此上下文中不允许说明符。

`mutable`说明符可以只能应用于类数据成员的名称，并不能应用于声明的名称`const`或`static`，并且不能应用引用成员。

## <a name="example"></a>示例

下面的示例演示如何 C2178 可能会发生，以及如何修复此错误。

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
