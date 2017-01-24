---
title: "准备用于运行调试可执行文件的测试计算机 | Microsoft Docs"
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
  - "调试可执行文件, 准备测试计算机以运行"
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 准备用于运行调试可执行文件的测试计算机
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要准备计算机测试由 Visual C\+\+ 生成的调试版应用程序，需要部署应用程序所依赖的Visual C\+\+动态链接库的调试版本。  若要确定已经部署了哪些动态链接库，请按照[了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)中列出的步骤进行操作。  特别的，Visual C\+\+ 动态链接库的调试版本的名称通常以“d”结尾；例如msvcr100.dll 的调试版本名为 msvcr100d.dll。  
  
> [!NOTE]
>  应用程序的调试版本是不可重新发布的，而且Visual C\+\+ 动态链接库的调试版本也都是不可重新发布的。  您可以将应用程序和 Visual C\+\+动态链接库的调试版本部署到的其他计算机，仅在未安装 Visual Studio 的计算机上调试和测试应用程序。  有关详细信息，请参阅[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
 部署调试版的 Visual C\+\+ 动态链接库和调试版的应用程序的方法有3种：  
  
-   通过使用包括应用程序正确的库版本和体系结构的合并模块的Setup项目，来集中部署来安装特定 Visual C\+\+ 动态链接库的调试版本到 %windir%\\system32\\目录下。  合并模块位于 Program Files或 Program Files \(x86\) 目录下的\\Common Files\\Merge Modules\\中。  合并模块的调试版本具有调试的名字，例如，Microsoft\_VC110\_DebugCRT\_x86.msm。  有关此部署的示例可参见[演练：使用安装项目部署 Visual C\+\+ 应用程序](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
-   在应用程序的安装目录下，通过 Program Files 或 Program Files \(x86\)下的\\Microsoft Visual Studio \<version\>\\VC\\redist\\Debug\_NonRedist\\中提供的文件，使用本地部署安装特定的 Visual C\+\+ 动态链接库的调试版本，。  
  
    > [!NOTE]
    >  若在另一台计算机上，使用 Visual C\+\+ 2005 或 Visual C\+\+ 2008对应用程序进行远程调试，则必须部署 Visual C\+\+ 动态链接库的调试版本作为共享的并行程序集。  可以使用Setup项目或 Windows Installer 安装相应的合并模块。  
  
-   在 Visual Studio 的**配置管理器** 对话框中使用**部署** 选项来复制项目输出和其他文件到远程计算机。  有关此部署的示例可参见[为 Visual Studio 项目设置远程调试](../Topic/Set%20Up%20Remote%20Debugging%20for%20a%20Visual%20Studio%20Project.md)。  
  
 安装 Visual C\+\+ 动态链接库后，可以在网络共享的情况下运行远程调试程序。  有关远程调试的更多信息，请参见[在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
## 请参阅  
 [在设备上安装远程工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Visual C\+\+ 中的部署](../ide/deployment-in-visual-cpp.md)   
 [Windows Installer 命令行选项](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [部署示例](../ide/deployment-examples.md)