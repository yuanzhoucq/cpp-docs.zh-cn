---
title: 编译器错误 C2381 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f09cd8c16eeb5ec797643cb6653d069df41b136
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076939"
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