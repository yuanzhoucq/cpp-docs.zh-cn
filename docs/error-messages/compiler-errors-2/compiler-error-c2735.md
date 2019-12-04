---
title: 编译器错误 C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 81ae9353709ddb5ab0d878e6dc157511d95a94fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755754"
---
# <a name="compiler-error-c2735"></a>编译器错误 C2735

不允许在形参类型说明符中使用 "关键字" 关键字

关键字在此上下文中无效。

下面的示例生成 C2735：

```cpp
// C2735.cpp
void f(inline int){}   // C2735
```
