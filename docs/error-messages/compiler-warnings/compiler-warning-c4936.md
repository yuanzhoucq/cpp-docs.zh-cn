---
title: 编译器警告 C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: 9b1c3d1de662451432fe4fa0f058c503dc1f7b39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220114"
---
# <a name="compiler-warning-c4936"></a>编译器警告 C4936

> 只有使用 /clr 或 /clr:pure 编译时，才支持此 __declspec

## <a name="remarks"></a>备注

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

**`__declspec`** 使用了修饰符，但只有在 **`__declspec`** 使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项之一编译时，修饰符才有效。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

始终发出 C4936 错误。  可以使用 [warning](../../preprocessor/warning.md) 杂注来禁用 C4936。

## <a name="example"></a>示例

下面的示例生成 C4936：

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```
