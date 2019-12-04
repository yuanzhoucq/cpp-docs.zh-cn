---
title: 编译器错误 C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760291"
---
# <a name="compiler-error-c2681"></a>编译器错误 C2681

"type"：名称的表达式类型无效

转换运算符尝试从无效的类型转换。 例如，如果使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)运算符将表达式转换为指针类型，则源表达式必须是指针。

下面的示例生成 C2681：

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
