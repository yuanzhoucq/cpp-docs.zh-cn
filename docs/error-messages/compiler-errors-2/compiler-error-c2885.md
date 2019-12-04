---
title: 编译器错误 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760923"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885

"class：： identifier"：在非类范围内不是有效的 using 声明

[使用](../../cpp/using-declaration.md)的声明不正确。

## <a name="example"></a>示例

此错误可能是由于对 Visual Studio 2005 执行的编译器一致性工作引起的，因为对嵌套类型具有 `using` 声明不再有效：必须显式限定对嵌套类型进行的每个引用，将类型置于命名空间中，或创建一个 typedef。

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

如果将 `using` 关键字与类成员一起使用， C++则需要在另一个类（派生类）中定义该成员。

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
