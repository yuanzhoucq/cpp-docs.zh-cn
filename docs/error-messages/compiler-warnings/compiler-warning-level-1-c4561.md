---
title: 编译器警告（等级 1）C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563782"
---
# <a name="compiler-warning-level-1-c4561"></a>编译器警告（等级 1）C4561

__fastcall 与不兼容 / clr 选项： 将转换为\__stdcall

[__Fastcall](../../cpp/fastcall.md)不能用于函数调用约定[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项。 编译器将忽略对调用`__fastcall`。 若要解决此警告，请删除对调用 **__fastcall**或不编译 **/clr**。

下面的示例生成 C4561:

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```