---
title: 编译器错误 C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: 8b311052d3a3525090d954c0dc8cee20e985b1b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632681"
---
# <a name="compiler-error-c2681"></a>编译器错误 C2681

type： 无效的表达式类型的名称

强制转换运算符尝试从无效的类型转换。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)运算符将表达式转换为指针类型，源表达式必须是指针。

下面的示例生成 C2681:

```
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```