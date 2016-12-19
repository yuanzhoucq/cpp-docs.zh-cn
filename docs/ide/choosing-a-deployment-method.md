---
title: "选择部署方法 | Microsoft Docs"
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
  - "应用程序部署 [C++], 方法"
  - "部署应用程序 [C++], 方法"
  - "DLL [C++], 重新分发"
  - "动态链接 [C++]"
  - "库 [C++], 应用程序部署问题"
  - "清单 [C++]"
  - "重新分发 DLL"
  - "并行程序集 [C++]"
  - "静态链接 [C++]"
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 选择部署方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除非你的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 应用程序是自包含的并且可使用复制命令部署，否则我们建议你使用 Windows Installer 进行部署。  Windows Installer 支持安装、修复和卸载，还支持应用程序文件、依赖项和注册表项的原子更新。  
  
> [!NOTE]
>  虽然在 Visual Studio 中可以进行 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 本机应用程序的 [ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md) 部署，但需要额外的步骤。  有关详细信息，请参阅 [Visual C\+\+ 应用程序的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
## Visual C\+\+ 库是共享的 DLL  
 由于 Visual C\+\+ 库由 Visual Studio 安装程序安装在 %windir%\\system32\\ 目录中，所以当你开发依赖这些库的 Visual C\+\+ 应用程序时，它会按预期运行。  但是，若要将应用程序部署到可能没有 Visual Studio 的计算机，我们建议你确保库与应用程序一起安装在这些计算机中。  
  
## 重新发布 Visual C\+\+ 库  
 在你的部署中，可以重新发布获得重新发布许可的任何版本的 Visual C\+\+ 库。  以下是三种部署方法：  
  
-   使用可再发行组件包进行集中部署，这些包将 Visual C\+\+ 库作为共享 DLL 安装在 %windir%\\system32\\ 中。（安装到该文件夹中需要管理员权限。）你可以创建一个脚本或安装程序，以便在目标计算机上安装应用程序之前运行可再发行组件包。  可再发行组件包可用于 x86、x64 和 ARM 平台（VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe）。  Visual Studio 将这些包放置在 %ProgramFiles\(x86\)%\\Microsoft Visual Studio `version`\\VC\\Redist\\`locale ID`\\ 中。  你还可以从 [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=132793)（Microsoft 下载中心）下载这些包。（在 Download Center（下载中心）上搜索与你的应用程序匹配的“[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] Redistributable Package *Visual Studio version and update*”。  例如，你使用了 Visual Studio 2012 Update 4 生成应用程序，则搜索“Visual C\+\+ Redistributable Package 2012 Update 4”。）有关如何使用可再发行组件包的信息，请参阅[演练：使用 Visual C\+\+ 可再发行组件包部署 Visual C\+\+ 应用程序](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
-   使用合并模块进行集中部署，其中每个模块会将特定的 Visual C\+\+ 库作为共享 DLL 安装在 %windir%\\system32\\ 中。（安装到该文件夹中需要管理员权限。）合并模块将成为你应用程序的 .msi 安装程序文件的一部分。  Visual C\+\+ 可再发行合并模块包含在 Visual Studio 的 \\Program Files \(x86\)\\Common Files\\Merge Modules\\ 中。  有关详细信息，请参阅[使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)。  
  
-   本地部署，你要复制 Visual Studio 安装中特定的 Visual C\+\+ DLL（一般位于 \\Program Files \(x86\)\\Microsoft Visual Studio `version`\\VC\\Redist\\`platform`\\`library`\\ 中），然后将其安装在目标计算机上应用程序可执行文件所在的文件夹中。  你可以使用该部署方法启用无管理员权限的用户的安装，或可从网络共享运行的应用程序的安装。  
  
 如果部署使用可再发行合并模块，并且由无管理员权限的用户运行安装，则 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL 不会安装，应用程序不会运行。  另外，通过允许按用户安装的合并模块生成的应用程序安装程序会将库安装在影响所有系统用户的共享位置中。  你可以使用本地部署在特定用户的应用程序目录中安装所需的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL，而不影响其他用户，也不需要管理员权限。  由于这可能造成可服务性问题，因此不建议本地部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可再发行 DLL。  
  
 Visual C\+\+ 库的错误部署可能导致执行依赖于这些库的应用程序时出现运行时错误。  操作系统加载应用程序时，会使用 [LoadLibraryEx](http://go.microsoft.com/fwlink/?LinkId=132792) 中介绍的搜索顺序。  
  
## 动态链接优于静态链接  
 我们建议你在重新发布 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库时避免使用静态链接。  虽然静态链接几乎从未显著提高应用程序性能，但却几乎总是增加服务的成本。  例如，一个应用程序静态链接到因安全性增强而更新的库，则除非应用程序进行重新编译和重新部署，否则不会从中受益。  因此我们建议你将应用程序动态链接到它们所依赖的库，以便在任何部署位置都能更新库。  
  
## 请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [选择部署策略](http://msdn.microsoft.com/zh-cn/ecd632d8-063c-4028-b785-81bba045107b)   
 [Windows Installer Deployment Overview](http://msdn.microsoft.com/zh-cn/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [ClickOnce 安全和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [部署示例](../ide/deployment-examples.md)