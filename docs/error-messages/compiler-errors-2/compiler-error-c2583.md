---
title: 编译器错误 C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: 0cb021dcba4d050afb943c03ba6b4dca053bcbb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206843"
---
# <a name="compiler-error-c2583"></a>编译器错误 C2583

"identifier"： "const/volatile" "this" 指针对于构造函数/析构函数是非法的

构造函数或析构函数被声明为 **`const`** 或 **`volatile`** 。 这是不允许的。

下面的示例生成 C2583：

```cpp
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```
