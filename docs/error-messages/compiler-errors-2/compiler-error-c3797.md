---
title: 编译器错误 C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 76206cdffce3f551ff472cbd83df486eb41ae80b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774823"
---
# <a name="compiler-error-c3797"></a>编译器错误 C3797

override： 事件声明不能具有重写说明符 （而应放置事件添加/remove/raise 方法相反）

不能覆盖另一个常用事件的普通事件 （事件，而不显式定义访问器方法）。 重写事件必须定义其行为与访问器函数。

有关详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3797。

```
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