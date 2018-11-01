---
title: 编译器错误 C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: e83380696aca3d6d45c235925b830bef9e3061a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544581"
---
# <a name="compiler-error-c3804"></a>编译器错误 C3804

property_accessor： 访问器方法的属性必须是全部静态或所有非静态

访问器函数时定义非 trivial 属性，可以是静态或实例，但不可同时使用两者。

有关更多信息，请参见 [property](../../windows/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

下面的示例生成 C3804。

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```