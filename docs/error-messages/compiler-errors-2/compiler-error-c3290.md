---
title: 编译器错误 C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: a7a73c13c28923761674294d8d6e601b95ffad96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760148"
---
# <a name="compiler-error-c3290"></a>编译器错误 C3290

“type”: 普通属性不能具有引用类型

未正确声明属性。 当声明普通属性时，编译器创建一个此属性将更新的变量，类中不能有跟踪引用变量。

有关详细信息，请参阅[属性](../../extensions/property-cpp-component-extensions.md)和[跟踪参考运算符](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3290。

```cpp
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```
