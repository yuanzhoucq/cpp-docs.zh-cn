---
title: 编译器错误 C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: 3bccfc723a9d62b794fa657e399bd94549448490
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755286"
---
# <a name="compiler-error-c3804"></a>编译器错误 C3804

"property_accessor"：属性的访问器方法必须是全部静态或全部非静态的

定义一个非常重要的属性时，访问器函数既可以是静态的，也可以是实例，但不能同时为两者。

有关更多信息，请参见 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

下面的示例生成 C3804。

```cpp
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
