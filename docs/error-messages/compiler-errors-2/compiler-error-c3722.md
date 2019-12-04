---
title: 编译器错误 C3722
ms.date: 11/04/2016
f1_keywords:
- C3722
helpviewer_keywords:
- C3722
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
ms.openlocfilehash: 08087b9cec0a48f0e439d6a2ff9fbe5f4e58d709
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753089"
---
# <a name="compiler-error-c3722"></a>编译器错误 C3722

不允许泛型事件

编译器仅允许泛型类、结构和函数。  有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)。

下面的示例生成 C3722：

```cpp
// C3722.cpp
// compile with: /clr
generic <typename T>
public delegate void MyEventHandler(System::Object^ sender, System::EventArgs^ e, T optional);

generic <class T>
public ref struct MyButton {
   generic<typename U>
   event MyEventHandler<U>^ Click;   // C3722
};
```
