---
title: 编译器错误 C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 7236cb75aef4250440a1e992415df07fb5b7da3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757171"
---
# <a name="compiler-error-c3797"></a>编译器错误 C3797

"override"：事件声明不能具有重写说明符（而应将其放在事件的 add/remove/raise 方法上）

不能使用另一个常用事件替代普通事件（没有显式定义的访问器方法的事件）。 重写事件必须定义其对访问器函数的行为。

有关详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3797。

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```
