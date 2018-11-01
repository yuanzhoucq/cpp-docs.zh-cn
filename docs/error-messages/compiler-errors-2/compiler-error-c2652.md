---
title: 编译器错误 C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464800"
---
# <a name="compiler-error-c2652"></a>编译器错误 C2652

identifier： 非法的复制构造函数： 第一个参数不能 identifier

复制构造函数中的第一个参数具有与类、 结构或联合为其定义相同的类型。 第一个参数可以是对类型而不是类型本身的引用。

下面的示例生成 C2651:

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```