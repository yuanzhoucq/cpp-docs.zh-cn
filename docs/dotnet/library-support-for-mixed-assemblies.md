---
title: "混合程序集的库支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "库 [C++], 混合程序集"
  - "混合程序集 [C++], 库支持"
  - "msvcm90[d].dll"
  - "msvcmrt[d].lib"
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合程序集的库支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支持针对用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译的应用程序使用标准 C\+\+ 库、公共运行库 \(CRT\)、ATL 和 MFC。  这使得使用这些库的现有应用程序也可以使用 .NET Framework 功能。  
  
 此项支持引入以下新 DLL 和导入库：  
  
-   Msvcmrt\[d\].lib，如果使用 \/clr 编译。  混合程序集链接到此导入库。  
  
-   Msvcm90\[d\].dll 和 Msvcurt\[d\].lib，如果使用 \/clr:pure 编译。  该 DLL 是提供托管 C 运行时 \(CRT\) 支持的混合程序集，并且是在全局程序集缓存 \(GAC\) 中安装的托管程序集的一部分。  纯程序集链接到此导入库并最终绑定到 Msvcm90.dll.。  
  
 此项支持有几个相关优点：  
  
-   CRT 和标准 C\+\+ 库可用于混合代码和纯代码。  提供的 CRT 和标准 C\+\+ 库是不可验证的；最终，调用与从本机代码使用一样仍旧路由到相同的 CRT 和标准 C\+\+ 库。  
  
-   纯映像和混合映像中的正确的统一异常处理。  
  
-   纯映像和混合映像中 C\+\+ 变量的静态初始化。  
  
-   对托管代码中的 per\-AppDomain 和 per\-process 变量的支持。  
  
-   解决 Visual C\+\+ .NET 和 Visual C\+\+ .NET 2003 中用于混合 DLL 的加载程序锁问题。  
  
 另外，此项支持有以下限制：  
  
-   只支持 CRT DLL 模型（无论是用 \/clr 还是 \/clr:pure 编译的代码）。  
  
-   如果纯对象和混合对象使用了 Visual C\+\+ 库，则无法在单个映像中混合这些对象（因为纯映像中的所有对象都必须是纯的）。  如果这样做，将会收到链接时错误。  
  
 应将公共语言运行时 \(CLR\) 更新到当前版本，因为不能保证早期版本也适用。  用这些更改生成的代码不能在 CLR 1.x 版本上运行。  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)