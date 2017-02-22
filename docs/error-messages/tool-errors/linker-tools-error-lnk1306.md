---
title: "链接器工具错误 LNK1306 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1306"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1306"
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 链接器工具错误 LNK1306
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法托管 DLL 入口点函数；编译为本机函数  
  
 不能将 DllMain 编译为 MSIL；必须将其编译为本机形式。  
  
 解决方法是：  
  
-   不使用 **\/clr** 编译包含入口点的文件。  
  
-   将入口点置于 `#pragma unmanaged` 节中。  
  
-   有关更多信息，请参见  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed、unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [运行库行为](../../build/run-time-library-behavior.md)  
  
## 示例  
 下面的示例生成 LNK1306。  
  
```  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```