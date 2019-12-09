---
title: 编译器错误 C2886
ms.date: 11/04/2016
f1_keywords:
- C2886
helpviewer_keywords:
- C2886
ms.assetid: c01588a1-484c-4dc9-a3f1-f900c6e44543
ms.openlocfilehash: a64457c84a48c73ad6714da01e48d41f3cc92efb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748718"
---
# <a name="compiler-error-c2886"></a>编译器错误 C2886

"class：： identifier"：符号不能用在成员 using 声明中

`using` 声明使用符号，如命名空间名称。 `using` 声明用于声明基类成员。

下面的示例生成 C2886：

```cpp
// C2886.cpp
// compile with: /c
namespace Z {
    int i;
}

class B {
protected:
    int i;
};

class D : public B {
    // Error: Z is a namespace
    using Z::i;   // C2886

    // OK: B is a base class
    using B::i;
};
```
