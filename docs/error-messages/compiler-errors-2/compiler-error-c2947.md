---
title: 编译器错误 C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 7056c13edca534701ffe82f0169897ea804f40d7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755351"
---
# <a name="compiler-error-c2947"></a>编译器错误 C2947

应为 ">" 以终止构造，却找到 "语法"

可能未正确终止泛型或模板自变量列表。

C2947 也可通过语法错误生成。

下面的示例生成 C2947：

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
