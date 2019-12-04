---
title: 编译器错误 C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 9cd46f7a8a0762fcae2bdec15b9b4be6384adb25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758679"
---
# <a name="compiler-error-c2273"></a>编译器错误 C2273

"type"： "->" 运算符右侧的非法

类型作为 `->` 运算符的右操作数显示。

尝试访问用户定义的类型转换可能会导致此错误。 使用关键字 `operator`-> 和 `type`之间。

下面的示例生成 C2273：

```cpp
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
