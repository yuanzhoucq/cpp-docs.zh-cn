---
title: 编译器警告（等级 4）C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: dee087b73bf032a68daf0527ea584efcc7579361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552628"
---
# <a name="compiler-warning-level-4-c4232"></a>编译器警告（等级 4）C4232

使用了非标准扩展: identifier: dllimport dllimport 地址不静态的不保证标识

在 Microsoft 扩展 (/Ze) 中，您可以赋予非静态值，像使用声明的函数地址**dllimport**修饰符。 在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，这将导致错误。

下面的示例生成 C4232:

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```