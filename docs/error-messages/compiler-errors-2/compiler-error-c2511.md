---
title: 编译器错误 C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: ff78cb50b274fe40d513739264bd7e9894bbed9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746560"
---
# <a name="compiler-error-c2511"></a>编译器错误 C2511

"identifier"：在 "class" 中找不到重载成员函数

未用指定参数声明函数的任何版本。  可能的原因：

1. 传递给函数的参数错误。

1. 传递的参数的顺序不正确。

1. 参数名称的拼写不正确。

下面的示例生成 C2511：

```cpp
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```
