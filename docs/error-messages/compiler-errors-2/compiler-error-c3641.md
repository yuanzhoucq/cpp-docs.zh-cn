---
title: 编译器错误 C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 44356fb1a1818a02102d23e6b308457f2f39506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200507"
---
# <a name="compiler-error-c3641"></a>编译器错误 C3641

> "*function*"：用/clr： pure 或/clr： safe 编译的函数的调用约定 "calling_convention" 无效

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

仅允许使用[/clr： pure](../../build/reference/clr-common-language-runtime-compilation.md) [__clrcall](../../cpp/clrcall.md)调用约定。

## <a name="example"></a>示例

下面的示例生成 C3641：

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
