---
title: 编译器错误 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 901e9b791616c5684b352c1fda7687f67b895d9c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447377"
---
# <a name="compiler-error-c2027"></a>编译器错误 C2027

使用了未定义类型 type

它定义之前，不能使用的类型。 若要解决此错误，请确保类型完全定义之前对其进行引用。

## <a name="example"></a>示例

下面的示例生成 C2027。

```
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

它是可以声明指向声明但未定义类型的指针。 但是C++不允许对未定义类型的引用。

下面的示例生成 C2027。

```
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