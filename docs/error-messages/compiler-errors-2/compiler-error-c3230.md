---
title: 编译器错误 C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: a4d5edeb5898a57b99839b7e044f909cea1ec199
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428244"
---
# <a name="compiler-error-c3230"></a>编译器错误 C3230

“function”：“template”的模板类型参数不能包含泛型类型参数：“param”

模板在编译时实例化，而泛型在运行时实例化。 因此，不能生成可调用模板的泛型代码，因为当泛型类型在最后才已知时，模板不能在运行时实例化。

以下示例生成 C3230：

```
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```