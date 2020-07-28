---
title: 编译器错误 C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 55c7f7ba8708e1475404a474f85df7dbe37fcec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220348"
---
# <a name="compiler-error-c2450"></a>编译器错误 C2450

"type" 类型的 switch 表达式是非法的

**`switch`** 表达式的计算结果为无效类型。 它的计算结果必须为整数类型或具有到整数类型的明确转换的类类型。 如果计算结果为用户定义类型，则必须提供转换运算符。

下面的示例生成 C2450：

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
