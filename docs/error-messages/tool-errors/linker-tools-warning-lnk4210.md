---
title: "链接器工具警告 LNK4210 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4e2d596527b60735b42fb4edfff6f36d0be808d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4210"></a>链接器工具警告 LNK4210  
  
> 部分*部分*存在; 现在，那里可能被未经处理的静态初始值设定项或终止符  
  
静态初始值设定项或终止符，引入了一些代码，但应用程序启动时，没有运行 VCRuntime 库启动代码或其等效项 （需要运行的静态初始值设定项或终止符）。 下面是代码的需要静态初始值设定项或终止符的一些示例：  
  
-   使用构造函数、 析构函数或虚函数表的全局类变量。  
  
-   使用非编译时常量初始化的全局变量。  
  
若要解决此问题，请尝试以下项之一：  
  
-   删除具有静态初始值设定项的所有代码。  
  
-   不要使用[/NOENTRY](../../build/reference/noentry-no-entry-point.md)。 删除 /NOENTRY 后，可能需要移除[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)在链接器命令行。  
  
-   如果你的生成使用 /MT，添加到链接器命令行 libcmt.lib、 libvcruntime.lib 和 libucrt.lib。 如果你的生成使用 /MTd，添加 libcmtd.lib、 vcruntimed.lib 和 libucrtd.lib。  
  
-   在将移动 /clr 时： 纯编译为 /clr，删除[/ENTRY](../../build/reference/entry-entry-point-symbol.md)从链接器行的选项。 这提供 CRT 初始化，并允许应用程序启动时执行的静态初始值设定项。  
  
 [/GS](../../build/reference/gs-buffer-security-check.md)编译器选项需要通过初始化`__security_init_cookie`函数。 默认情况下，在中运行的 VCRuntime 库启动代码中提供此初始化`_DllMainCRTStartup`。  
  
-   如果你的项目使用 /ENTRY，生成和 /ENTRY 以外传递函数`_DllMainCRTStartup`，该函数必须调用`_CRT_INIT`初始化 CRT。 如果 DLL 使用 /GS、 需要静态初始值设定项，或在 MFC 或 ATL 代码的上下文中调用此单独的调用是不够的。 请参阅[Dll 和 Visual c + + 运行库行为](../../build/run-time-library-behavior.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)