---
title: 编译器错误 C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 7f3568aa5dfee116a225256a4452465c05f72f6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759147"
---
# <a name="compiler-error-c2283"></a>编译器错误 C2283

“identifier”：未命名的结构上不允许使用纯说明符或抽象重写说明符

使用纯说明符声明了未命名类或结构的成员函数，这是不允许的。

以下示例生成 C2283：

```cpp
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```
