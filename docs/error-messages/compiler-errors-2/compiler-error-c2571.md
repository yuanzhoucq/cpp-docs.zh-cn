---
title: 编译器错误 C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: d7d4898e5f0b55c50a4c18cef053cc150394d7e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485067"
---
# <a name="compiler-error-c2571"></a>编译器错误 C2571

function： 虚函数不能为联合 union 中

联合被声明具有虚拟函数。 您可以声明只能在类或结构中的虚拟函数。  可能的解决方法：

1. 更改为类或结构的并集。

1. 使非虚拟函数。

下面的示例生成 C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```