---
title: 编译器错误 C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 2d015bd165986467a82f33a2ae0dda08c6f6d248
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744142"
---
# <a name="compiler-error-c2450"></a>编译器错误 C2450

"type" 类型的 switch 表达式是非法的

`switch` 表达式的计算结果为无效类型。 它的计算结果必须为整数类型或具有到整数类型的明确转换的类类型。 如果计算结果为用户定义类型，则必须提供转换运算符。

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
