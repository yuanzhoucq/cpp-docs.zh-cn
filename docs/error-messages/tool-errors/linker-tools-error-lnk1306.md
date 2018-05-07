---
title: 链接器工具错误 LNK1306 |Microsoft 文档
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
ms.openlocfilehash: bb340a4c28f94f18e0c4b65bea8749394e002bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1306"></a>链接器工具错误 LNK1306  
  
> 不能管理 DLL 入口点函数;编译为本机  
  
`DllMain` 不能编译为 MSIL;它必须编译为本机。  
  
若要解决此问题，  
  
-   包含入口点，而无需将文件编译 **/clr**。  
  
-   将入口点放在`#pragma unmanaged`部分。  
  
有关详细信息，请参见:  
  
-   [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed, unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [DLL 和 Visual C++ 运行时库行为](../../build/run-time-library-behavior.md)  
  
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
  
若要解决此问题，并不使用 /clr 选项来编译此文件，或使用`#pragma`指令，用于将入口点定义放非托管的部分中，在此示例中所示：  
  
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
