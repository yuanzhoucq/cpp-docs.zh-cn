---
title: 编译器错误 C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 2697ce5a790fffe762d97ca3380853514de6d437
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220257"
---
# <a name="compiler-error-c2682"></a>编译器错误 C2682

无法使用 casting_operator 从 "type1" 转换为 "type2"

转换运算符尝试在不兼容的类型之间进行转换。 例如，不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)运算符来转换指向引用的指针。 **`dynamic_cast`** 运算符不能用于转换远离限定符。 类型上的所有限定符都必须匹配。

可以使用 **`const_cast`** 运算符删除 **`const`** 、或等属性 **`volatile`** **`__unaligned`** 。

下面的示例生成 C2682：

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

下面的示例生成 C2682：

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
