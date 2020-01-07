---
title: 编译器错误 C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: b1345fbb44558db01b19eec04b64cf7aa036931a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301920"
---
# <a name="compiler-error-c2142"></a>编译器错误 C2142

函数声明不同，仅在其中一个中指定了变量参数

函数的一个声明包含变量参数列表。 其他声明不存在。 仅限 ANSI C （[/za](../../build/reference/za-ze-disable-language-extensions.md)）。

下面的示例生成 C2142：

```c
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```
