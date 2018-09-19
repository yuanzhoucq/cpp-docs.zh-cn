---
title: 编译器错误 C2885 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf47d830980b9fb93481f575e3e3a806ce8bbf68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035690"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885

class::identifier： 不是有效使用的声明在非类范围内

所用[使用](../../cpp/using-declaration.md)声明不正确。

## <a name="example"></a>示例

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： 将不再有效具有`using`声明嵌套的类型，则必须显式限定对嵌套类型，将类型放在名称中进行的每个引用空间，或创建一个 typedef。

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

如果使用`using`类的成员，c + + 关键字需要定义该成员在另一个类 （派生类）。

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