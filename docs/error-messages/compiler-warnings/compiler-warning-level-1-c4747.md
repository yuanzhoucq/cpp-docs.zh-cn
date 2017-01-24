---
title: "编译器警告（等级 1）C4747 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4747"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4747"
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4747
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用托管“entrypoint”: 托管代码可能未运行在加载程序锁下，包括 DLL 入口点和从 DLL 入口点访问到的调用  
  
 编译器找到编译为 MSIL 的（可能）DLL 入口点。由于加载入口点已编译为 MSIL 的 DLL 时存在一些潜在问题，因此强烈建议不要将 DLL 入口点函数编译为 MSIL。  
  
 有关更多信息，请参见[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)和[链接器工具错误 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。  
  
### 更正此错误  
  
1.  不要使用 **\/clr** 编译该模块。  
  
2.  使用 `#pragma unmanaged` 标记入口点函数。  
  
## 示例  
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