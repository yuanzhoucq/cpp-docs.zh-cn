---
title: 编译器错误 C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 0b53e704c14746579a32550726364c062a9ade6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756742"
---
# <a name="compiler-error-c3073"></a>编译器错误 C3073

"type"： ref 类没有用户定义的复制构造函数

在[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)编译中，编译器不会为引用类型生成复制构造函数。 在任何 **/clr**编译中，如果需要复制类型的实例，则必须为引用类型定义自己的复制构造函数。

有关详细信息，请参阅[ C++引用类型的堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>示例

下面的示例生成 C3073。

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
