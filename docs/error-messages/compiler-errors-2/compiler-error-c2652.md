---
title: 编译器错误 C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756118"
---
# <a name="compiler-error-c2652"></a>编译器错误 C2652

"identifier"：非法的复制构造函数：第一个参数不能是 "identifier"

复制构造函数中的第一个参数的类型与定义它的类、结构或联合的类型相同。 第一个参数可以是对类型的引用，但不能是类型本身。

下面的示例生成 C2651：

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
