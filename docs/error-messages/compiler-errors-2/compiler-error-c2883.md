---
title: 编译器错误 C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: cb6b1043d976cfeb8cb92c8780c5b84ea9700b8b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760949"
---
# <a name="compiler-error-c2883"></a>编译器错误 C2883

"name"：函数声明与 using 声明引入的 "identifier" 冲突

尝试多次定义函数。 第一次定义是从具有 `using` 声明的命名空间中进行的。 第二个是本地定义。

下面的示例生成 C2883：

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
