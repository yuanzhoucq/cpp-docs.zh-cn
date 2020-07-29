---
title: 编译器警告（等级 1）C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: fe8ae1f8ef8180f2d3c5ba9ae2401b9447b22527
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230631"
---
# <a name="compiler-warning-level-1-c4561"></a>编译器警告（等级 1）C4561

"__fastcall" 与 "/clr" 选项不兼容：转换为 " \_ _stdcall"

[__Fastcall](../../cpp/fastcall.md)函数调用约定不能与[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项一起使用。 编译器将忽略对的调用 **`__fastcall`** 。 若要修复此警告，请删除对的调用 **`__fastcall`** 或不带 **/clr**编译的。

下面的示例生成 C4561：

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
