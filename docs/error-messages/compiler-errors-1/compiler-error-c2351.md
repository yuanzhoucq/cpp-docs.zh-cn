---
title: 编译器错误 C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 2d93902ee0008a54da1b2ecf165e0a829362511f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665486"
---
# <a name="compiler-error-c2351"></a>编译器错误 C2351

已过时的 c + + 构造函数初始化语法

在新式的初始化列表中的构造函数，必须显式命名每个直接基类，即使它是唯一的基类。

下面的示例生成 C2351:

```
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```