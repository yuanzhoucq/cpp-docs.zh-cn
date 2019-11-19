---
title: 编译器警告（等级1） C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: b0fd27142f0404a53fa2fee87fb2309e2f54d2c2
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965977"
---
# <a name="compiler-warning-level-1-c4561"></a>编译器警告（等级1） C4561

"__fastcall" 与 "/clr" 选项不兼容：转换为 "\__stdcall"

[__Fastcall](../../cpp/fastcall.md)函数调用约定不能与[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项一起使用。 编译器忽略对 `__fastcall`的调用。 若要修复此警告，请删除对 **__fastcall**或不带 **/clr**编译的调用。

下面的示例生成 C4561：

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```