---
title: 编译器错误 C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749095"
---
# <a name="compiler-error-c3900"></a>编译器错误 C3900

"member"：不允许在当前范围内使用

属性块只能包含函数声明和内联函数定义。 属性块中不允许除函数之外的其他成员。 不允许使用 typedef、运算符或友元函数。 有关详细信息，请参阅 [property](../../extensions/property-cpp-component-extensions.md)。

事件定义只能包含访问方法和函数。

下面的示例生成 C3900：

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

下面的示例生成 C3900：

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
