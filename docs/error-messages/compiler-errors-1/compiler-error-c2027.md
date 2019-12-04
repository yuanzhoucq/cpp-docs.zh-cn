---
title: 编译器错误 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750996"
---
# <a name="compiler-error-c2027"></a>编译器错误 C2027

使用了未定义的类型 "type"

在定义类型之前，无法使用该类型。 若要解决此错误，请确保在引用类型之前已完全定义了该类型。

## <a name="example"></a>示例

下面的示例生成 C2027。

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>示例

可以声明指向已声明但未定义类型的指针。 但C++不允许引用未定义的类型。

下面的示例生成 C2027。

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
