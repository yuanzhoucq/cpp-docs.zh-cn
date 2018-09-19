---
title: 编译器警告 （等级 1） C4561 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4561
dev_langs:
- C++
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0770a8b8b42c8174d421f55dd45ff7f335d06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115783"
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