---
title: 编译器警告（等级 1）C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616250"
---
# <a name="compiler-warning-level-1-c4630"></a>编译器警告（等级 1）C4630

symbol: extern 存储类说明符在成员定义上非法

数据成员或成员函数定义为`extern`。 成员不能为外部，尽管可以整个对象。 编译器将忽略`extern`关键字。 下面的示例生成 C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```