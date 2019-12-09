---
title: 编译器错误 C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 78a42b264129ee365e664b1242c8aa58dd1244bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758471"
---
# <a name="compiler-error-c3919"></a>编译器错误 C3919

"event_method"：函数必须是 "type" 类型

未正确声明事件访问器方法。

有关事件的详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

下面的示例生成 C3919：

```cpp
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```
