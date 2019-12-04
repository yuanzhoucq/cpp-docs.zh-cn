---
title: 编译器错误 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756027"
---
# <a name="compiler-error-c2663"></a>编译器错误 C2663

"function"：数字重载没有 "this" 指针的合法转换

编译器无法将 `this` 转换为成员函数的任何重载版本。

此错误的原因可能是对 `const` 对象调用了非`const` 成员函数。  可能的解决方法：

1. 从对象声明中删除 `const`。

1. 将 `const` 添加到其中一个成员函数重载。

下面的示例生成 C2663：

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
