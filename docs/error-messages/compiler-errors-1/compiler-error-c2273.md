---
title: 编译器错误 C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f2ed5c49a9f8243fd5c9c302caf2876493c26bc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526348"
---
# <a name="compiler-error-c2273"></a>编译器错误 C2273

“type”: 位于“->”运算符右边时非法

一种类型显示为右操作数`->`运算符。

通过尝试访问用户定义类型转换可以导致此错误。 请在 -> 和 `operator` 之间使用关键字 `type`。

下面的示例生成 C2273:

```
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```