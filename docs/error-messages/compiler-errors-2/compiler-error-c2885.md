---
title: 编译器错误 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 9b6b7bb54d5dce48dc6fce517eb0c909b0284da2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233439"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885

"class：： identifier"：在非类范围内不是有效的 using 声明

[使用](../../cpp/using-declaration.md)的声明不正确。

## <a name="example"></a>示例

此错误可能是由于对 Visual Studio 2005 执行的编译器一致性工作所导致的，因为对 **`using`** 嵌套类型的声明不再有效; 您必须显式限定对嵌套类型的每个引用，将该类型放入命名空间中，或创建一个 typedef。

下面的示例生成 C2885。

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>示例

如果将关键字用于 **`using`** 类成员，c + + 要求在另一个类（派生类）内部定义该成员。

下面的示例生成 C2885。

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
