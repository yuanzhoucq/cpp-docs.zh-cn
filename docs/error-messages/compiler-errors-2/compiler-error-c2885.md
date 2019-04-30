---
title: 编译器错误 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388762"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885

class::identifier： 不是有效使用的声明在非类范围内

所用[使用](../../cpp/using-declaration.md)声明不正确。

## <a name="example"></a>示例

视觉对象执行的编译器一致性工作可以导致此错误C++2005年： 不再有效能够`using`声明嵌套的类型，则必须显式限定对嵌套类型，将类型放进行的每个引用在命名空间，或创建一个 typedef。

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