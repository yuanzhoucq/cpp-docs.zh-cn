---
title: 链接器工具错误 LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: ddaa8797e0cf8ff617408aedc770b21cc656cec4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160453"
---
# <a name="linker-tools-error-lnk1306"></a>链接器工具错误 LNK1306

> DLL 入口点函数不能进行管理;编译为本机

`DllMain` 不能编译为 MSIL;必须为本机编译。

若要解决此问题，

- 包含入口点，而无需将文件编译 **/clr**。

- 将入口点放在`#pragma unmanaged`部分。

有关详细信息，请参见:

- [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)

- [managed, unmanaged](../../preprocessor/managed-unmanaged.md)

- [混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)

- [DLL 和 Visual C++ 运行时库行为](../../build/run-time-library-behavior.md)

## <a name="example"></a>示例

下面的示例生成 LNK1306。

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

若要解决此问题，请执行不使用 /clr 选项编译此文件中，或使用`#pragma`指令以将入口点定义放在非托管部分中，在此示例中所示：

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
