---
title: 编译器错误 C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: 1477c767b770e4d1498df951d7ef5b4448e6fde7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536732"
---
# <a name="compiler-error-c2292"></a>编译器错误 C2292

identifier： 最好的条件继承表示形式: representation1，但 representation2 所需声明

编译以下代码[/vmb](../../build/reference/vmb-vmg-representation-method.md) ("最有利情况下始终"表示形式) 导致 C2292。

```
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```