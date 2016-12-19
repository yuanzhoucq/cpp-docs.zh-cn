---
title: "Visual C++ 应用程序的 ClickOnce 部署 | Microsoft Docs"
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
  - "部署应用程序 [C++], [ClickOnce]"
  - "应用程序部署 [C++], ClickOnce"
  - "ClickOnce 部署 [C++], C++ 应用程序"
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 应用程序的 ClickOnce 部署
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 提供了两种不同技术用来部署 Windows 应用程序：ClickOnce 部署和 [Windows Installer](http://msdn.microsoft.com/library/cc185688) 部署。  
  
## C\+\+ 中的 ClickOnce 部署  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 部署环境不直接支持使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目，但提供了使用它的工具。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 在 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 开发环境中支持 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)]。  如果你的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目是 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 项目的依赖项，则可以从 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 开发环境中使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署发布该应用程序（包括其依懒项）。  
  
 若要使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 应用程序，首先必须使用 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) 或其图形用户界面版本（有关信息，请参见[MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)）生成 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)和 [ClickOnce 部署清单](../Topic/ClickOnce%20Deployment%20Manifest.md)。  
  
 首先使用 Mage.exe 生成应用程序清单；其结果文件具有扩展名 .manifest。  然后使用 Mage.exe 生成部署清单；其结果文件具有扩展名 .application。  然后对清单签名。  
  
 应用程序清单必须指定目标处理器（**“x86”**、**“x64”**或**“ARM”**）。  有关这些选项的信息，请参见 [部署 64 位应用程序的必备组件](../Topic/Deploying%20Prerequisites%20for%2064-bit%20Applications.md)。  
  
 此外，应用程序和部署清单的名称必须不同于 C\+\+ 应用程序的名称。  这样可避免由 Mage.exe 创建的应用程序清单与作为 C\+\+ 应用程序一部分的外部清单之间发生冲突。  
  
 你的部署将需要安装应用程序所依赖的所有 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库。  要确定特定应用程序的依赖项，可以使用 depends.exe 或带有 \/DEPENDENTS 选项的 DUMPBIN 实用工具。  有关依赖项的更多信息，请参见 [了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。  你可能需要运行 VCRedist.exe；此实用工具在目标计算机上安装 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库。  
  
 你可能还需要为应用程序生成引导程序（必备安装程序）以部署必备组件；有关引导程序的信息，请参见 [创建引导程序包](../Topic/Creating%20Bootstrapper%20Packages.md)。  
  
 有关此技术的更为详细的说明，请参见 [ClickOnce 安全和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  有关 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署的详细示例，请参见[演练：手动部署 ClickOnce 应用程序](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)。  
  
## 请参阅  
 [Mage.exe（清单生成和编辑工具）](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe（证书创建工具）](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [部署应用程序、服务器和组件](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/zh-cn/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [ClickOnce 安全和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [创建引导程序包](../Topic/Creating%20Bootstrapper%20Packages.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)