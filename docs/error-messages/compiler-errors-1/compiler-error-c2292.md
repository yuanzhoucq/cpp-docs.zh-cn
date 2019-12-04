---
title: 编译器错误 C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: 82d381fddc4cafd364bc0e45e70e5fb5c1cb3d84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759108"
---
# <a name="compiler-error-c2292"></a>编译器错误 C2292

"identifier"：最佳 case 继承表示形式： "representation1" 已声明，但需要 "representation2"

用[/vmb](../../build/reference/vmb-vmg-representation-method.md) （"最佳情况总是" 表示形式）编译以下代码会导致 C2292。

```cpp
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```
