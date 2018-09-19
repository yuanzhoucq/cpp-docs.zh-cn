---
title: 编译器错误 C3797 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3797
dev_langs:
- C++
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ac1ded1c95f7e8bea9598e468010c75d8bd917a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033415"
---
# <a name="compiler-error-c3797"></a>编译器错误 C3797

override： 事件声明不能具有重写说明符 （而应放置事件添加/remove/raise 方法相反）

不能覆盖另一个常用事件的普通事件 （事件，而不显式定义访问器方法）。 重写事件必须定义其行为与访问器函数。

有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。

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