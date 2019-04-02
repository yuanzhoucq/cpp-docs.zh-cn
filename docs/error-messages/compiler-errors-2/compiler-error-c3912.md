---
title: 编译器错误 C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: bd66196c35715304577b8f6785261be8bdcdafec
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773393"
---
# <a name="compiler-error-c3912"></a>编译器错误 C3912

event： 事件的类型必须是委托类型

事件声明，但不是正确的类型。

有关详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

下面的示例生成 C3912:

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```