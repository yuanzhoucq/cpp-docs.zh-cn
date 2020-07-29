---
title: 编译器错误 C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: aa55392e9f58caa4292cf5f96ef97f65a53bf913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207948"
---
# <a name="compiler-error-c2441"></a>编译器错误 C2441

> "*variable*"：使用 __declspec （process）声明的符号必须是/clr： pure 模式中的常量

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

默认情况下，变量位于 **/clr： pure**下的每个应用程序域中。 `__declspec(process)`如果在一个应用程序域中修改并读取另一个应用程序域中的，则在 **/clr： pure**下标记的变量容易出现错误。

因此，编译器强制每个进程变量 **`const`** 在 **/clr： pure**下，使其仅在所有应用程序域中都是只读的。

有关详细信息，请参阅[进程](../../cpp/process.md)和[/Clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
