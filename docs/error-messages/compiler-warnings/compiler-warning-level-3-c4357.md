---
title: 编译器警告（等级 3）C4357
ms.date: 11/04/2016
f1_keywords:
- C4357
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
ms.openlocfilehash: a7923fdcda2a781c9680f8b3753fd101c73be19c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402016"
---
# <a name="compiler-warning-level-3-c4357"></a>编译器警告（等级 3）C4357

param 数组参数的形式自变量列表中的委托 del 生成 function 时，忽略

`ParamArray`属性被忽略，和`function`不能使用变量参数调用。

下面的示例生成 C4357:

```
// C4357.cpp
// compile with: /clr /W3 /c
using namespace System;
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357

public delegate void g(int i, array<Object^>^ varargs);   // OK
```