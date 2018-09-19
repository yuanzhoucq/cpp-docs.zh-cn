---
title: 编译器错误 C2466 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d43ee9d09fba77db022177a06c6ebe95c65ff79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037835"
---
# <a name="compiler-error-c2466"></a>编译器错误 C2466

不能分配常量大小为 0 的数组

分配或使用大小为零声明数组时。 数组大小的常量表达式必须是大于零的整数。 与零个下标的数组声明是合法的仅对类、 结构或联合成员的和仅可与 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

下面的示例生成 C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```