---
title: 编译器错误 C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367923"
---
# <a name="compiler-error-c2675"></a>编译器错误 C2675

一元 operator: type 不定义该运算符或到可接受类型转换到预定义的运算符

当使用一元运算符，也会发生 C2675 和类型未定义操作员或可接受的类型转换到预定义的运算符。 要使用该运算符，必须针对指定类型将其重载，或者定义一个到某个类型（该运算符已针对此类型进行了定义）的转换。

## <a name="example"></a>示例

下面的示例生成 C2675。

```
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```