---
title: 编译器错误 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: a36655b0b3a28536538998656d7ce354c409d07c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225522"
---
# <a name="compiler-error-c2381"></a>编译器错误 C2381

"function"：重定义;__declspec （noreturn）不同

已声明一个函数，然后定义该函数，但定义使用了[noreturn](../../cpp/noreturn.md) **`__declspec`** 修饰符。 使用 `noreturn` 构成函数的重定义; 声明和定义需要同意使用的 `noreturn` 。

下面的示例生成 C2381：

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
