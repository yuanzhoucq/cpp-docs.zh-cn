---
title: 编译器警告（等级 1）C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 2fd7f0960966a981d82d19e7b2533b1ffcd3bc00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175189"
---
# <a name="compiler-warning-level-1-c4747"></a>编译器警告（等级 1）C4747

调用托管的 "entrypoint"：托管代码可能未在加载程序锁下运行，包括 DLL 入口点和从 DLL 入口点访问的调用

编译器找到了编译为 MSIL 的（可能的） DLL 入口点。  由于加载已编译为 MSIL 的 DLL 的潜在问题，强烈建议您不要将 DLL 入口点函数编译为 MSIL。

有关详细信息，请参阅[混合程序集](../../dotnet/initialization-of-mixed-assemblies.md)和[链接器工具的初始化错误 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 不要用 **/clr**编译模块。

1. 将入口点函数标记 `#pragma unmanaged`。

## <a name="example"></a>示例

下面的示例生成 C4747。

```cpp
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
