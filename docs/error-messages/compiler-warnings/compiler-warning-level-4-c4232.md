---
title: 编译器警告（等级 4）C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173915"
---
# <a name="compiler-warning-level-4-c4232"></a>编译器警告（等级 4）C4232

使用了非标准扩展： "identifier"： dllimport "dllimport" 的地址不是静态的，不保证标识

在 Microsoft 扩展（/Ze）下，可以提供非静态值作为使用**dllimport**修饰符声明的函数的地址。 在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，这会导致错误。

下面的示例生成 C4232：

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
