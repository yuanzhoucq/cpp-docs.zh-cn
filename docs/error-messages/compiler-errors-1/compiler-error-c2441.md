---
title: 编译器错误 C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205304"
---
# <a name="compiler-error-c2441"></a>编译器错误 C2441

> "*variable*"：使用 __declspec （process）声明的符号必须是/clr： pure 模式中的常量

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

默认情况下，变量位于 **/clr： pure**下的每个应用程序域中。 如果在一个应用程序域中修改并读取另一个应用程序域中的，则在 **/clr： pure**下标记为 `__declspec(process)` 的变量容易出现错误。

因此，编译器强制每个进程变量在 **/clr： pure**下 `const`，使其仅在所有应用程序域中都是只读的。

有关详细信息，请参阅[进程](../../cpp/process.md)和[/Clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
