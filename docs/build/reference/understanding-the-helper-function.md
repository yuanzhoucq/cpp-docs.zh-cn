---
title: "了解 Helper 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>了解 Helper 函数
链接器支持延迟加载 helper 函数是什么实际上在运行时加载 DLL。 你可以修改要自定义其行为，通过编写自己的函数，并将其链接到你的程序而不是在 Delayimp.lib 中使用提供的帮助器函数的帮助器函数。 一个帮助器函数提供所有延迟加载 Dll。  
  
 如果你想要执行的 DLL 或导入的名称所基于的特定处理，你可以提供您自己的 helper 函数版本。  
  
 Helper 函数执行下列操作：  
  
-   检查以查看已加载的库的存储句柄  
  
-   调用**LoadLibrary**尝试加载的 DLL  
  
-   调用**GetProcAddress**尝试获取的过程的地址  
  
-   返回到延迟导入加载转换 （thunk） 来调用当前加载的入口点  
  
 Helper 函数可以回调到你的程序中的通知挂钩后的每个以下操作：  
  
-   Helper 函数启动时  
  
-   之前**LoadLibrary**帮助器函数中调用  
  
-   之前**GetProcAddress**帮助器函数中调用  
  
-   如果调用**LoadLibrary**帮助器函数中失败  
  
-   如果调用**GetProcAddress**帮助器函数中失败  
  
-   函数完成后帮助器处理  
  
 其中每个挂钩点可返回一个值，将更改以某种方式除为延迟导入负载转换 （thunk） 返回的帮助器例程的正常处理。  
  
 默认帮助程序代码可以 Delayhlp.cpp 和 Delayimp.h 中找到 （在 vc\include)，并且在 Delayimp.lib 中编译 （以 vc\lib)。 你将需要在编译中包括此库，除非你编写您自己的 helper 函数。  
  
 以下主题介绍 helper 函数：  
  
-   [自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [调用约定、参数和返回类型](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [结构和常量定义](../../build/reference/structure-and-constant-definitions.md)  
  
-   [计算所需值](../../build/reference/calculating-necessary-values.md)  
  
-   [卸载延迟加载的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)