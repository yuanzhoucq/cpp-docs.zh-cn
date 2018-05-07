---
title: 准备测试计算机以运行调试可执行文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33683ebe349fbfdcb3fd51179ed6bc3140510c00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>准备用于运行调试可执行文件的测试计算机
若要准备计算机以测试使用 Visual C++ 生成的应用程序的调试版本，你必须部署应用程序依赖的 Visual C++ 库 DLL 的调试版本。 若要确定哪些 Dll 必须部署，请按照中的步骤[了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 通常，Visual C++ 库 DLL 的调试版本具有以“d”结尾的名称；例如，msvcr100.dll 的调试版本名为 msvcr100d.dll。  
  
> [!NOTE]
>  应用程序的调试版本是不可再发行的，而且 Visual C++ 库 DLL 的调试版本也是不可再发行的。 你可以只是为了在未安装 Visual Studio 的计算机上调试和测试应用程序，来仅将应用程序的调试版本和 Visual C++ DLL 部署到其他计算机上。 有关详细信息，请参阅 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。  
  
 可通过三种方式将 Visual C++ 库 DLL 的调试版本与应用程序的调试版本一起部署。  
  
-   借助中央部署将特定的 Visual C++ DLL 的调试版本安装到 %windir%\system32\ 目录中，方式是使用包含正确的库版本的合并模块和应用程序的体系结构的安装程序项目。 在 Program Files 或 Program Files (x86) \common 模块目录中找到合并模块\\。 合并模块的调试版本的名称包含 Debug，例如，Microsoft_VC110_DebugCRT_x86.msm。 此部署的一个示例可能位于[演练： 部署 Visual c + + 应用程序通过使用安装项目](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
-   使用本地部署通过使用在 Program Files 或 Program Files (x86) \Microsoft Visual Studio 中的目录中提供的文件在应用程序的安装目录中安装特定的 Visual c + + DLL 的调试版本\<版本 >\VC\redist\Debug_NonRedist\\。  
  
    > [!NOTE]
    >  对于在其他计算机上对使用 Visual C++ 2005 或 Visual C++ 2008 生成的应用程序进行远程调试，您必须将 Visual C++ 库 DLL 的调试版本部署为共享的并行程序集。 可以使用安装程序项目或 Windows Installer 来安装相应的合并模块。  
  
-   使用**部署**选项**Configuration Manager** Visual Studio 将项目输出和其他文件复制到远程计算机中的对话框。 
  
 安装 Visual C++ DLL 之后，您可以在网络共享上运行远程调试程序。 有关远程调试的详细信息，请参阅[远程调试](/visualstudio/debugger/remote-debugging.md)。  
  
## <a name="see-also"></a>请参阅  
 
 [Visual c + + 中的部署](../ide/deployment-in-visual-cpp.md)   
 [Windows 安装程序命令行选项](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [部署示例](../ide/deployment-examples.md)[远程调试](/visualstudio/debugger/remote-debugging.md)