---
title: 编译器错误 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f9746ecb41e873fb1d929a939c78f1817dc0e2f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220270"
---
# <a name="compiler-error-c2663"></a>编译器错误 C2663

"function"：数字重载没有 "this" 指针的合法转换

编译器无法转换 **`this`** 为成员函数的任何重载版本。

此错误可能是由于调用对象上的非 **`const`** 成员函数导致的 **`const`** 。  可能的解决方法：

1. **`const`** 从对象声明中移除。

1. 添加 **`const`** 到成员函数重载之一。

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
