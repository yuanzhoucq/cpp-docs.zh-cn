---
title: 编译器错误 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 868d43e0796b7a6ab7398573e8b61efcb627d8a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761720"
---
# <a name="compiler-error-c3174"></a>编译器错误 C3174

未指定模块特性

使用视觉对象C++属性的程序还不使用[module](../../windows/module-cpp.md)属性，此属性在任何使用属性的程序中都是必需的。

下面的示例生成 C3174：

```cpp
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```
