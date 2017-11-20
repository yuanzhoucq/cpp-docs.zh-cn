---
title: "部署本机桌面应用程序 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a8dcf4a49813ae108edb23b50676e751db5e2f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="deploying-native-desktop-applications-visual-c"></a>部署本机桌面应用程序 (Visual C++)
部署是用于分配要安装到其他计算机上的已完成应用程序或组件的进程。 当在开发人员计算机上创建了应用程序时开始部署规划。 当已安装并准备好在用户计算机上运行应用程序时，部署结束。  
  
 Visual Studio 提供用于部署 Windows 应用程序的不同技术。 其中包括 ClickOnce 部署和 Windows Installer 部署。  
  
-   可以使用 ClickOnce 来部署 c + + 应用程序面向公共语言运行时 (CLR)-混合、 纯代码和可验证程序集。 尽管你可以使用 Windows Installer 部署托管的应用程序，我们建议你使用 ClickOnce，因为它利用.NET Framework 安全功能，如清单签名。 ClickOnce 不支持本机 c + + 应用程序部署。 有关详细信息，请参阅 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
-   Windows Installer 技术可以用于部署本机 C++ 应用程序或面向 CLR 的 C++ 应用程序。  
  
 文档本部分中的文章讨论如何确保本机 Visual C++ 应用程序可在任何提供受支持的目标平台的计算机上运行，安装包内必须包括哪些文件以及重新分发应用程序所依赖的组件的建议方式。  
  
## <a name="in-this-section"></a>本节内容  
 [Visual C++ 中的部署](../ide/deployment-in-visual-cpp.md)  
  
 [部署概念](../ide/deployment-concepts.md)  
  
 [了解 Visual C++ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)  
  
 [确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md)  
  
 [选择部署方法](../ide/choosing-a-deployment-method.md)  
  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)  
  
 [部署示例](../ide/deployment-examples.md)  
  
 [重新分发 Web 客户端应用程序](../ide/redistributing-web-client-applications.md)  
  
 [Visual C++ 应用程序的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)  
  
 [在以前的运行时版本上运行 c + + /clr 应用程序](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)  
  
## <a name="related-sections"></a>相关章节  
 [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
 [部署](/dotnet/framework/deployment/index)  
  
 [C/C++ 独立应用程序和并行程序集疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)