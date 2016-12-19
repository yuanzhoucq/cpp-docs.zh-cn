---
title: "生成 C/C++ 独立应用程序和并行程序集 | Microsoft Docs"
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
  - "独立的应用程序 [C++]"
  - "WinSxS [C++]"
  - "本机程序集缓存 [C++]"
  - "生成 [C++], 独立应用程序"
  - "并行应用程序 [C++]"
  - "生成 [C++], 并行程序集"
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成 C/C++ 独立应用程序和并行程序集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支持 Windows 客户端应用程序的部署模型，其理论基础是[独立应用程序](http://msdn.microsoft.com/library/aa375190)和[并行程序集](_win32_side_by_side_assemblies)。 默认情况下，Visual C\+\+ 将所有本机 C\/C\+\+ 应用程序都作为独立应用程序来生成，这些应用程序使用[清单](http://msdn.microsoft.com/library/aa375365)来描述其在 Visual C\+\+ 库上的依赖关系。  
  
 将 C\/C\+\+ 程序生成为独立应用程序具有一系列的好处。 例如，当其他 C\/C\+\+ 应用程序安装或卸载 Visual C\+\+ 库时，不会影响独立应用程序。 仍可将独立应用程序使用的 Visual C\+\+ 库重新发布到应用程序的本地文件夹中或通过安装重新发布到本机程序集缓存 \(WinSxS\)；但是，通过使用[发布者配置文件](http://msdn.microsoft.com/library/aa375680)，为已部署的应用程序提供 Visual C\+\+ 库服务时会更加简单。 借助于独立应用程序部署模型，更加容易确保在特定计算机上运行的 C\/C\+\+ 应用程序使用 Visual C\+\+ 库的最新版本，同时使系统管理员和应用程序的作者仍可以控制应用程序与其依赖 DLL 的显式版本绑定。  
  
 本节讨论如何将 C\/C\+\+ 应用程序生成为独立应用程序并确保使用清单将它绑定到 Visual C\+\+ 库。 本部分中的信息主要适用于本机或非托管的 Visual C\+\+ 应用程序。 有关部署使用 Visual C\+\+ 生成的本机应用程序的信息，请参阅[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## 本节内容  
 [独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)  
  
 [生成 C\/C\+\+ 独立应用程序](../build/building-c-cpp-isolated-applications.md)  
  
 [生成 C\/C\+\+ 并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)  
  
 [如何：生成免注册 COM 组件](../build/how-to-build-registration-free-com-components.md)  
  
 [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
 [了解 C\/C\+\+ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)  
  
 [疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
## 相关章节  
 [独立应用程序和并行程序集](http://msdn.microsoft.com/library/dd408052)  
  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)