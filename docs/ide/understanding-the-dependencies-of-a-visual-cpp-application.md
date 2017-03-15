---
title: "了解 Visual C++ 应用程序的依赖项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "应用程序部署 [C++], 依赖项"
  - "依赖项 [C++], 应用程序部署与"
  - "Dependency Walker"
  - "depends.exe"
  - "部署应用程序 [C++], 依赖项"
  - "DLL [C++], 依赖项"
  - "DUMPBIN 实用工具"
  - "库 [C++], 应用程序部署问题"
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 了解 Visual C++ 应用程序的依赖项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以查看项目属性来确定应用程序依赖于哪些 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库。  （在解决方案资源管理器中，右键单击该项目并选择**“属性”**以打开**“属性页”**对话框。） 你还可以使用 Dependency Walker \(depends.exe\)，以更全面地了解依赖项。  
  
 在**“属性页”**对话框中，你可以检查**“配置属性”**下的各个页面，以了解依赖项。  例如，如果你的项目使用 MFC 库并且你在**“配置属性”**、**“常规”**页面上选择**“使用 MFC”**、**“在共享 DLL 中使用 MFC”**，则你的应用程序在运行时依赖于 MFC DLL（如 mfc\<version\>.dll）。  如果你的应用程序不使用 MFC，而你在**“配置属性”**\-\>**“C\/C\+\+”**\-\>**“代码生成”**页面上选择**“运行库”**为**“多线程调试 DLL \(\/MDd\)”**或**“多线程 DLL \(\/MD\)”**，则它可能依赖于 CRT 库。  
  
 确定应用程序依赖哪些 DLL 的更全面的方式是：使用 Dependency Walker \(depends.exe\) 打开该应用程序。  可以从 [Dependency Walker](http://go.microsoft.com/fwlink/p/?LinkId=132640) 网站下载该工具。  
  
 通过使用 depends.exe，可以检查在加载时链接到应用程序的 DLL 的列表及延迟加载的 DLL 的列表。  如果要获取在运行时动态加载的 DLL 的完整列表，可在 depends.exe 中使用分析功能来测试应用程序，直到你确定所有代码路径都已执行过。  在结束分析会话时，depends.exe 将显示在运行时动态加载了哪些 DLL。  
  
 使用 depends.exe 时，请注意，一个 DLL 可能依赖于另一个 DLL 或特定版本的 DLL。  可以在开发计算机上或目标计算机上使用 Depends.exe。  在开发计算机上，Depends.exe 将报告支持应用程序所需要的 DLL。  如果在目标计算机上运行应用程序时遇到问题，可以将 depends.exe 复制到计算机上，然后在该工具中打开应用程序，以便确定是否有任何必要的 DLL 丢失或不正确。  
  
 在你知道应用程序所依赖的 DLL 后，就可以在将应用程序部署到另一个计算机时确定哪些 DLL 必须与其一起重新发布。  在大多数情况下，你不必重新发布系统 DLL，但是可能必须重新发布 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库的 DLL。  有关详细信息，请参阅[确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md)。  
  
## 请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)