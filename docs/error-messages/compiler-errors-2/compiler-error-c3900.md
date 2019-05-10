---
title: 编译器错误 C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345408"
---
# <a name="compiler-error-c3900"></a>编译器错误 C3900

member： 不允许在当前范围内

属性块可以包含函数声明和内联函数定义。 在属性块中不允许函数之外的任何成员。 不允许使用任何 typedef、 运算符或友元函数。 有关详细信息，请参阅 [property](../../extensions/property-cpp-component-extensions.md)。

事件定义只能包含访问方法和函数。

下面的示例生成 C3900:

```
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

下面的示例生成 C3900:

```
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