---
title: 编译器错误 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303484"
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

它是可以声明指向声明但未定义类型的指针。  但 VisualC++不允许对未定义类型的引用。

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