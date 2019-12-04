---
title: 编译器错误 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749030"
---
# <a name="compiler-error-c3908"></a>编译器错误 C3908

访问级别的限制低于 "构造"

与属性本身上指定的访问权限相比，属性访问器方法（get 或 set）的访问限制更少。  同样，对于事件访问器方法。

有关详细信息，请参阅[属性](../../extensions/property-cpp-component-extensions.md)和[事件](../../extensions/event-cpp-component-extensions.md)。

下面的示例生成 C3908：

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```
