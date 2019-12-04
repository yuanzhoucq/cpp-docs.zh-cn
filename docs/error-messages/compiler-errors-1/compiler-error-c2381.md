---
title: 编译器错误 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745390"
---
# <a name="compiler-error-c2381"></a>编译器错误 C2381

"function"：重定义;__declspec （noreturn）不同

已声明一个函数，然后定义该函数，但定义使用了[noreturn](../../cpp/noreturn.md) `__declspec` 修饰符。 使用 `noreturn` 构成函数的重定义;声明和定义需要同意使用 `noreturn`。

下面的示例生成 C2381：

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
