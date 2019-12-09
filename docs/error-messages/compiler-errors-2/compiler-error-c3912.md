---
title: 编译器错误 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: 9054124cbfe2d86c062c6e97651bd69eebe5471c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748744"
---
# <a name="compiler-error-c3912"></a>编译器错误 C3912

"event"：事件类型必须是委托类型

已声明事件，但它的类型不正确。

有关详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

下面的示例生成 C3912：

```cpp
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```
