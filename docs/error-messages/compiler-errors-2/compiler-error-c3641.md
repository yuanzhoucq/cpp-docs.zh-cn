---
title: 编译器错误 C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: f6c27067e4f07c89b4226cf4d26adf2afb0b07ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385649"
---
# <a name="compiler-error-c3641"></a>编译器错误 C3641

> '*函数*： 使用 /clr 编译的函数的调用约定 calling_convention 无效： pure 或 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

仅[__clrcall](../../cpp/clrcall.md)调用约定允许用于[/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C3641:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```