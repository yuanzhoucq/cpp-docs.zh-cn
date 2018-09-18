---
title: 链接器工具错误 LNK1306 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc007a4a594c8593d7820365377f1c811b1e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050562"
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
