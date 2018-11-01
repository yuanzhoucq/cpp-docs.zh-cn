---
title: 编译器错误 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: b29f7dac6c6d71e12eb0f003cdfc151dd2c349a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663175"
---
# <a name="compiler-error-c2381"></a>编译器错误 C2381

function： 重定义;__declspec （noreturn） 不同

函数声明，但然后已定义但是所使用的定义[noreturn](../../cpp/noreturn.md) `__declspec`修饰符。 利用`noreturn`构成了该函数的重定义; 的声明和定义需要达成一致的使用`noreturn`。

下面的示例生成 C2381:

```
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```