---
title: 编译器错误 C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 90bc30460cb578d1ed2812e40907a361eeb3b039
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748419"
---
# <a name="compiler-error-c2635"></a>编译器错误 C2635

无法将 "identifier1 *" 转换为 "identifier2\*";隐含从虚拟基类的转换

转换需要将 `virtual` 基类强制转换为派生类，这是不允许的。

下面的示例生成 C2635：

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
