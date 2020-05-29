---
title: 编译器警告（等级 1）C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 11a1bcdc8396b1eb74121c27154b8c6c24fa92a6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162278"
---
# <a name="compiler-warning-level-1-c4561"></a>编译器警告（等级 1）C4561

"__fastcall" 与 "/clr" 选项不兼容：转换为 "\__stdcall"

[__Fastcall](../../cpp/fastcall.md)函数调用约定不能与[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项一起使用。 编译器忽略对 `__fastcall`的调用。 若要修复此警告，请删除对 **__fastcall**或不带 **/clr**编译的调用。

下面的示例生成 C4561：

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
