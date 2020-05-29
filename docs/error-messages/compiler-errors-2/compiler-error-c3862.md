---
title: 编译器错误 C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165478"
---
# <a name="compiler-error-c3862"></a>编译器错误 C3862

> "*function*"：不能使用/clr： pure 或/clr： safe 编译非托管函数

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

使用 **/clr： pure**或 **/clr： safe**进行编译将生成仅包含 MSIL 的映像，而不会生成一个无本机（非托管）代码的映像。  因此，不能在 **/clr： pure**或 **/clr： safe**编译中使用 `unmanaged` 杂注。

有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[托管的非托管](../../preprocessor/managed-unmanaged.md)。

## <a name="example"></a>示例

下面的示例生成 C3862：

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
