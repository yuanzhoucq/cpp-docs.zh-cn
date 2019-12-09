---
title: 编译器错误 C2805
ms.date: 11/04/2016
f1_keywords:
- C2805
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
ms.openlocfilehash: 500660d70616a530fce3d8674f0f116ce219d1d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760629"
---
# <a name="compiler-error-c2805"></a>编译器错误 C2805

二元运算符 "operator operator" 的参数太少

二元运算符没有参数。

下面的示例生成 C2805：

```cpp
// C2805.cpp
// compile with: /c
class X {
public:
   X operator< ( void );   // C2805 must take one parameter
   X operator< ( X );   // OK
};
```
