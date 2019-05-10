---
title: 编译器错误 C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338917"
---
# <a name="compiler-error-c2441"></a>编译器错误 C2441

> '*变量*： 使用 __declspec （process） 声明的符号必须是常量在 /clr: pure 模式

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

默认情况下，变量是每个应用程序域下 **/clr: pure**。 变量标记`__declspec(process)`下 **/clr: pure**容易发生错误，如果在另一个应用程序域中修改读。

因此，编译器可强制每个进程的变量是`const`下 **/clr: pure**，使其读取仅在所有应用程序域中的。

有关详细信息，请参阅[进程](../../cpp/process.md)并[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```