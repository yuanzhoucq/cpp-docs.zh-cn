---
title: 编译器错误 C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446236"
---
# <a name="compiler-error-c3862"></a>编译器错误 C3862

> '*函数*： 不能编译非托管的函数使用 /clr: pure 或 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

使用编译 **/clr: pure**或 **/clr: safe**会生成一个唯一 MSIL 映像，具有没有本机 （非托管） 代码的映像。  因此，不能使用`unmanaged`中的杂注 **/clr: pure**或 **/clr: safe**编译。

有关详细信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)并[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。

## <a name="example"></a>示例

下面的示例生成 C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```