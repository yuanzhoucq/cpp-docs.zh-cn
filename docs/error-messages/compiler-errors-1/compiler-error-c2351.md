---
title: 编译器错误 C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 6839d0c44efa10ba9507389fea35964fa748d646
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759966"
---
# <a name="compiler-error-c2351"></a>编译器错误 C2351

过时C++的构造函数初始化语法

在构造函数的新样式初始化列表中，必须显式命名每个直接基类，即使它是唯一的基类。

下面的示例生成 C2351：

```cpp
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```
