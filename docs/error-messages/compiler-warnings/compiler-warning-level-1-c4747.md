---
title: 编译器警告 （等级 1） C4747 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285819"
---
# <a name="compiler-warning-level-1-c4747"></a>编译器警告（等级 1）C4747
调用托管入口点： 不会在有加载程序锁，包括 DLL 入口点和调用从 DLL 入口点达到运行托管的代码  
  
 编译器发现一个 （可能） 编译为 MSIL 的 DLL 入口点。  由于加载的 DLL 的入口点编译为 MSIL 的潜在问题，你已从编译为 MSIL DLL 入口点函数，强烈建议不要使用。  
  
 有关详细信息，请参阅[初始化混合程序集的](../../dotnet/initialization-of-mixed-assemblies.md)和[链接器工具错误 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  对模块进行不编译 **/clr**。  
  
2.  将标记与入口点函数`#pragma unmanaged`。  
  
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