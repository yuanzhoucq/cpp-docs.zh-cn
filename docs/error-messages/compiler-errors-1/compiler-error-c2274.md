---
title: 编译器错误 C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: f2fcb75098f18ad113ba68959035b37d9cddd6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667020"
---
# <a name="compiler-error-c2274"></a>编译器错误 C2274

type： 非法的右边。 ' 运算符

类型显示为成员访问 （.） 运算符的右操作数。

通过尝试访问用户定义类型转换可以导致此错误。 使用关键字`operator`之间的这段和`type`。

下面的示例生成 C2286：

```
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```