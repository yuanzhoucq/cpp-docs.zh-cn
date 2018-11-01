---
title: 编译器警告（等级 1）C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462382"
---
# <a name="compiler-warning-level-1-c4747"></a>编译器警告（等级 1）C4747

调用托管入口点： 托管的代码可能无法运行在有加载程序锁，包括 DLL 入口点和调用从 DLL 入口点访问

编译器发现一个 （可能） 编译为 MSIL 的 DLL 入口点。  由于加载的 DLL 的入口点编译为 MSIL 的潜在问题，您都强烈建议您不要编译为 MSIL DLL 入口点函数。

有关详细信息，请参阅[混合程序集初始化](../../dotnet/initialization-of-mixed-assemblies.md)并[链接器工具错误 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 对模块进行不编译 **/clr**。

1. 将标记与入口点函数`#pragma unmanaged`。

## <a name="example"></a>示例

下面的示例生成 C4747。

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```