---
title: "部署概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序部署 [C++], 关于应用程序部署"
  - "依赖项 [C++], 应用程序部署与"
  - "部署应用程序 [C++], 关于部署应用程序"
  - "库 [C++], 应用程序部署问题"
  - "Windows Installer [C++]"
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 部署概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本节讨论部署 C\+\+ 应用程序的主要注意事项。  
  
## C\+\+ 中的 Windows Installer 部署  
 Visual C\+\+ 项目通常使用传统的 Windows Installer 安装进行部署。  若要准备部署 Windows Installer，需要将应用程序打包到 setup.exe 文件中，并将该文件与安装程序包 \(.msi\) 一起分发。  用户随后可以运行 setup.exe 来安装应用程序。  
  
 应用程序的打包是通过将安装项目添加到解决方案来实现的：当生成时，将创建分发给用户的安装和安装程序包文件。  有关更多信息，请参见[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
## 库依赖项  
 当使用 Visual C\+\+ 库提供的功能生成 C\/C\+\+ 应用程序时，该应用程序在运行时将依赖于那些库的存在。  为了让应用程序运行，它必须以静态或动态方式链接到必需的 Visual C\+\+ 库。  如果应用程序动态链接到某个 Visual C\+\+ 库，则在运行应用程序时，该库必须存在以便可以加载它。  另一方面，如果应用程序静态链接到某个 Visual C\+\+ 库，则它不要求在用户的计算机上存在相应的 DLL。  但是，静态链接具有某些负面影响，如增加应用程序文件的大小并使得维护有可能更难进行。  有关更多信息，请参见[使用 DLL 的优点](../build/advantages-of-using-dlls.md)。  
  
## 打包和重新发布  
 Visual C\+\+ 库以 DLL 形式打包，C\/C\+\+ 应用程序所有必需的库都由 Visual Studio 安装在开发人员的计算机上。  但在将应用程序部署到用户时，要求他们为了运行您的应用程序而安装 Visual Studio，这在大多数情况下是不可行的。  这使得仅重新发布应用程序正确运行所需的 Visual C\+\+ 的部分变得非常重要。  
  
 有关打包和重新发布的更多信息，请参见下列主题：  
  
-   [确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md).  
  
-   [选择部署方法](../ide/choosing-a-deployment-method.md).  
  
 有关部署示例和故障排除的建议，请参见：  
  
-   [部署示例](../ide/deployment-examples.md).  
  
-   [疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
## 请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/zh-cn/121be21b-b916-43e2-8f10-8b080516d2a0)