---
title: 编译器错误 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: ff5e770052301e95f694d3712f95b82732c2faba
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447697"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885

class::identifier： 不是有效使用的声明在非类范围内

所用[使用](../../cpp/using-declaration.md)声明不正确。

## <a name="example"></a>示例

为 Visual Studio 2005 执行的编译器一致性工作可以生成此错误： 将不再有效具有`using`声明嵌套的类型，则必须显式限定对嵌套类型，将类型放在 n 中进行的每个引用amespace，或创建一个 typedef。

下面的示例生成 C2885。

```
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

如果您使用`using`关键字与一个类成员， C++ ，必须先定义该成员在另一个类 （派生类）。

下面的示例生成 C2885。

```
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