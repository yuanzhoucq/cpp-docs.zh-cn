---
title: 编译器错误 C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: fd807dedb6c300860611d07212b8fc8952a90a65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758666"
---
# <a name="compiler-error-c2274"></a>编译器错误 C2274

"type"： "." 运算符右侧的非法

类型显示为成员访问（.）运算符的右操作数。

尝试访问用户定义的类型转换可能会导致此错误。 在句点和 `type`之间使用关键字 `operator`。

下面的示例生成 C2286：

```cpp
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
