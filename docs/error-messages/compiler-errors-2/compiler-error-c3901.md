---
title: 编译器错误 C3901
ms.date: 11/04/2016
f1_keywords:
- C3901
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
ms.openlocfilehash: 0c5b561f0e650ace69e09d33942f2036b9ee91ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677261"
---
# <a name="compiler-error-c3901"></a>编译器错误 C3901

accessor_function： 必须具有返回类型 type

至少一个 get 方法的返回类型必须与属性类型匹配。 有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。

下面的示例生成 C3901:

```
// C3901.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String^ Name {
      void get();   // C3901
      // try the following line instead
      // String^ get();
   };
};

ref class Y {
   property double values[int, int] {
      int get(int, int);   // C3901
      // try the following line instead
      // double get(int, int);
   };
};
```