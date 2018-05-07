---
title: 部署概念 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4fa40373e268c76caca17f3466573bc3e830757
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="deployment-concepts"></a>部署概念
本部分讨论部署 c + + 应用程序的主要注意事项。  
  
## <a name="windows-installer-deployment-in-c"></a>在 c + + 的 Windows Installer 部署  
 Visual c + + 项目通常会使用传统的 Windows Installer 安装程序以进行部署。 若要准备的 Windows Installer 部署，打包应用程序中的 setup.exe 文件，并将该文件，与安装程序包 (.msi) 一起分发。 用户然后运行 setup.exe 来安装你的应用程序。  
  
 通过将安装程序项目添加到解决方案; 打包应用程序生成时，它创建的安装程序和安装程序将分发给用户的包文件。 有关详细信息，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
## <a name="library-dependencies"></a>库依赖项  
 C/c + + 应用程序生成时使用的 Visual c + + 库所提供功能，它将依赖于这些库在运行时的状态。 为了使运行该应用程序，它必须链接，静态还是动态，到必要的 Visual c + + 库。 如果应用程序动态链接到 Visual c + + 库，则在运行该库时必须存在以便可以加载它。 另一方面，如果应用程序静态链接到 Visual c + + 库，然后它不需要相应的 Dll 存在于用户的计算机上。 静态链接中，但是，具有某些负面影响，如增加应用程序文件的大小并使得维护有可能更难。 有关详细信息，请参阅[使用 Dll 的优点](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)。  
  
## <a name="packaging-and-redistributing"></a>打包和重新发布  
 Visual c + + 库打包为 Dll，并且 C/c + + 应用程序的所有必要的库可以由 Visual Studio 安装在开发人员计算机上。 但是，当你将应用部署到你的用户，不能在大多数情况下，要求他们安装 Visual Studio，才能运行你的应用程序。 务必要能够重新分发的部分的 Visual c + + 所需的应用程序正常运行。  
  
 有关打包和重新分发的详细信息，请参阅以下主题：  
  
-   [确定哪些 Dll 重新分发的](../ide/determining-which-dlls-to-redistribute.md)。  
  
-   [选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
 有关部署示例和有关故障排除建议，请参阅：  
  
-   [部署示例](../ide/deployment-examples.md)。  
  
-   [疑难解答 C/c + + 独立应用程序和通过并行程序集](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Windows Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)