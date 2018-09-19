---
title: 编译器警告 （等级 C4232 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 450c764cfc130acf28e3edfb40fcd17c8ac3b664
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118279"
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