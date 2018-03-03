---
title: "Visual c + + 应用程序的 ClickOnce 部署 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1a036a1520a747448c5541f367f0b43711e30b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Visual C++ 应用程序的 ClickOnce 部署
Visual Studio 提供两种不同技术用于部署 Windows 应用程序： ClickOnce 部署或[Windows Installer](http://msdn.microsoft.com/library/cc185688)部署。  
  
## <a name="clickonce-deployment-in-c"></a>C++ 中的 ClickOnce 部署  
 Visual c + + 开发环境不直接支持的使用 ClickOnce，Visual c + + 项目的部署，但工具可供使用它。  
  
> [!NOTE]
>  Visual Studio 在 Visual C# 和 Visual Basic 开发环境中支持 ClickOnce。 如果你的 Visual c + + 项目的 Visual C# 项目依赖项，你可以发布应用程序 （包括其依赖项） 使用 ClickOnce 部署从 Visual C# 开发环境。  
  
 若要部署使用 ClickOnce 的 Visual c + + 应用程序，首先需要生成[ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)和[ClickOnce 部署清单](/visualstudio/deployment/clickonce-deployment-manifest)使用[Mage.exe （清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)或其图形用户界面版本 (有关信息，请参阅[MageUI.exe （清单生成和编辑工具，图形化客户端）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client))。  

  
 首先使用 Mage.exe 生成应用程序清单；其结果文件具有扩展名 .manifest。 然后使用 Mage.exe 生成部署清单；其结果文件具有扩展名 .application。 然后对清单签名。  
  
 应用程序清单必须指定目标处理器 (**x86**， **x64**，或**ARM**)。 请参阅[64 位应用程序的部署先决条件](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)有关这些选项的信息。  
  
 此外，应用程序和部署清单的名称必须不同于 C++ 应用程序的名称。 这样可避免由 Mage.exe 创建的应用程序清单与作为 C++ 应用程序一部分的外部清单之间发生冲突。  
  
 你的部署将需要安装你的应用程序所依赖的任何 Visual c + + 库。 要确定特定应用程序的依赖项，可以使用 depends.exe 或带有 /DEPENDENTS 选项的 DUMPBIN 实用工具。 依赖项的详细信息，请参阅[了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 你可能需要运行 VCRedist.exe;此实用程序在目标计算机上安装 Visual c + + 库。  
  
 你可能还需要为你的应用程序部署必备组件; 生成引导程序 （系统必备组件安装程序）引导程序的信息，请参阅[创建引导程序包](/visualstudio/deployment/creating-bootstrapper-packages)。  
  
 该技术的更多详细说明，请参阅[ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 ClickOnce 部署的详细示例，请参阅[演练： 手动部署 ClickOnce 应用程序](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)。  
  
## <a name="see-also"></a>请参阅  
 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Makecert.exe（证书创建工具）](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [部署应用程序、 服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Windows Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)   
 [创建引导程序包](/visualstudio/deployment/creating-bootstrapper-packages)   
 [.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)