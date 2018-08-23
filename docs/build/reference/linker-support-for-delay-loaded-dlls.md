---
title: 链接器延迟加载 Dll 的支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aea4ca6d5391f71f27d59d0192fcf1f832dd6702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375579"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>链接器的延迟加载 DLL 支持
Visual c + + 链接器现在支持 Dll 的延迟的加载。 这使您需要使用 Windows SDK 函数**LoadLibrary**和**GetProcAddress**来实现延迟加载的 DLL。  
  
 在 Visual c + + 6.0 中之前, 在运行时加载 DLL 的唯一方法是通过使用**LoadLibrary**和**GetProcAddress**; 操作系统将加载 DLL 时可执行文件或 DLL 使用已加载。  
  
 从开始 Visual c + + 6.0 中，静态链接的 DLL 时，链接器提供了选项延迟加载 DLL，直到该程序调用该 DLL 中的函数。  
  
 应用程序可以延迟加载 DLL 使用[/DELAYLOAD （延迟加载导入）](../../build/reference/delayload-delay-load-import.md)与帮助器函数 （Visual c + + 提供的默认实现） 的链接器选项。 Helper 函数将加载的 DLL 在运行时通过调用**LoadLibrary**和**GetProcAddress**为你。  
  
 你应考虑延迟加载 DLL，如果：  
  
-   你的程序不可能在 DLL 中调用的函数。  
  
-   DLL 中的函数可能不会调用直到较晚的程序的执行。  
  
 可以在下列任一工具的生成过程中指定 DLL 的延迟的加载。EXE 或。DLL 项目。 答:。延迟的一个或多个 Dll 加载的 DLL 项目不应本身调用延迟加载的入口点位于 Dllmain 中。  
  
 以下主题介绍延迟加载 Dll:  
  
-   [指定要延迟加载的 DLL](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [显式卸载延迟加载的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [加载被延迟加载的 DLL 的所有导入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [绑定导入](../../build/reference/binding-imports.md)  
  
-   [错误处理和通知](../../build/reference/error-handling-and-notification.md)  
  
-   [转储延迟加载的导入](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [延迟加载 DLL 的约束](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [了解 Helper 函数](understanding-the-helper-function.md)  
  
-   [开发自己的 Helper 函数](../../build/reference/developing-your-own-helper-function.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 中的 Dll](../../build/dlls-in-visual-cpp.md)   
 [链接](../../build/reference/linking.md)