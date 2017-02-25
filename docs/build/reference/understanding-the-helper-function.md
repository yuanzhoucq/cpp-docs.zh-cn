---
title: "了解 Helper 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__delayLoadHelper 函数"
  - "__delayLoadHelper2 函数"
  - "DLL 的延迟加载, Helper 函数"
  - "delayhlp.cpp"
  - "delayimp.h"
  - "delayimp.lib"
  - "Helper 函数"
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 了解 Helper 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

链接器支持的延迟加载 Helper 函数是在运行时实际加载 DLL 的函数。  您可以不用 Delayimp.lib 中提供的 Helper 函数，而是编写自己的函数，并链接到您的程序来修改 Helper 函数以自定义它的行为。  一个 Helper 函数服务于所有延迟加载的 DLL。  
  
 如果想执行基于 DLL 名称或导入名称的特定处理，可以提供自己的 Helper 函数版本。  
  
 Helper 函数执行下列操作：  
  
-   检查存储的库句柄，确保已加载。  
  
-   调用 **LoadLibrary** 以尝试加载 DLL。  
  
-   调用 **GetProcAddress** 以尝试获取过程的地址。  
  
-   返回到延迟导入加载 thunk，以调用当前加载的入口点。  
  
 执行完下列每一操作后，Helper 函数可以回调程序中的通知挂钩：  
  
-   Helper 函数启动时  
  
-   只有当在 Helper 函数中调用 **LoadLibrary** 之前  
  
-   只有当在 Helper 函数中调用 **GetProcAddress** 之前  
  
-   如果在 Helper 函数中调用 **LoadLibrary** 失败  
  
-   如果在 Helper 函数中调用 **GetProcAddress** 失败  
  
-   Helper 函数完成处理后  
  
 这些挂钩点中的每一个都可以返回一个值，该值将以某种方式改变 Helper 例程的正常处理（返回到延迟导入加载 thunk 除外）。  
  
 默认 Helper 代码在 Delayhlp.cpp 和 Delayimp.h（在 vc\\include 中）中可以找到，并在 Delayimp.lib（在 vc\\lib 中）中编译。  除非编写自己的 Helper 函数，否则需要在编译中包括该库。  
  
 下列主题描述 Helper 函数：  
  
-   [自 Visual C\+\+ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [调用约定、参数和返回类型](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [结构和常数定义](../../build/reference/structure-and-constant-definitions.md)  
  
-   [计算所需值](../../build/reference/calculating-necessary-values.md)  
  
-   [卸载延迟加载的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)