---
title: 选择部署方法 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdf024f75f03b55465ccd15670c47d3c761e56e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338661"
---
# <a name="choosing-a-deployment-method"></a>选择部署方法
我们建议你使用 Windows Installer 进行部署，除非你的 Visual C++ 应用程序是自包含的并且可使用复制命令部署。 Windows Installer 支持安装、修复和卸载，还支持应用程序文件、依赖项和注册表项的原子更新。  
  
> [!NOTE]
>  虽然在 Visual Studio 中可以进行 Visual C++ 本机应用程序的 [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) 部署，但需要额外的步骤。 有关详细信息，请参阅 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++ 库是共享的 DLL  
 由于 Visual C++ 库由 Visual Studio 安装程序安装在 %windir%\system32\ 目录中，所以当你开发依赖这些库的 Visual C++ 应用程序时，它会按预期运行。 但是，若要将应用程序部署到可能没有 Visual Studio 的计算机，我们建议你确保库与应用程序一起安装在这些计算机中。  
  
## <a name="redistributing-visual-c-libraries"></a>重新发布 Visual C++ 库  
 在你的部署中，可以重新发布获得重新发布许可的任何版本的 Visual C++ 库。 以下是三种部署方法：  
  
-   使用可再发行组件包进行集中部署，这些包将 Visual C++ 库作为共享 DLL 安装在 %windir%\system32\\ 中。 （安装到该文件夹中需要管理员权限。）你可以创建一个脚本或安装程序，以便在目标计算机上安装应用程序之前运行可再发行组件包。 可再发行组件包可用于 x86、x64 和 ARM 平台（VCRedist_x86.exe、VCRedist_x64.exe 或 VCRedist_arm.exe）。 Visual Studio 将这些包放置在 %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\ 中。 你还可以从 [Microsoft 下载中心](http://go.microsoft.com/fwlink/p/?linkid=132793)下载这些包。 （使用下载中心的搜索框搜索与你的应用程序匹配的“Visual C++ 可再发行组件包 Visual Studio 版本和更新”。 例如，若使用 Visual Studio 2015 Update 3 生成应用程序，则搜索“Visual C++ Redistributable Package 2015 Update 3”。）若要详细了解如何使用可再发行组件包，请参阅[演练：使用 Visual C++ 可再发行包部署 Visual C++ 应用程序](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
-   使用合并模块进行集中部署，其中每个模块会将特定的 Visual C++ 库作为共享 DLL 安装在 %windir%\system32\\ 中。 （安装到该文件夹中需要管理员权限。）合并模块将成为你应用程序的 .msi 安装程序文件的一部分。 Visual C++ 可再发行合并模块包含在 Visual Studio 的 \Program Files (x86)\Common Files\Merge Modules\\ 中。 有关详细信息，请参阅[使用合并模块重新分发](../ide/redistributing-components-by-using-merge-modules.md)。  
  
-   在本地部署中，你要复制 Visual Studio 安装中特定的 Visual C++ DLL（一般位于 \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\ 中），然后将其安装在目标计算机上应用程序可执行文件所在的文件夹中。 你可以使用该部署方法启用无管理员权限的用户的安装，或可从网络共享运行的应用程序的安装。  
  
 如果部署使用可再发行合并模块，并且由不具备管理员权限的用户运行安装，则 Visual C++ DLL 不会安装，应用程序也不会运行。 另外，通过允许按用户安装的合并模块生成的应用程序安装程序会将库安装在影响所有系统用户的共享位置中。 你可以使用本地部署在特定用户的应用程序目录中安装所需的 Visual C++ DLL，这样不影响其他用户，也不需要管理员权限。 由于这可能造成可服务性问题，因此不建议本地部署 Visual C++ 可再发行 DLL。  
  
 Visual C++ 库的错误部署可能导致执行依赖于这些库的应用程序时出现运行时错误。 操作系统加载应用程序时，会使用 [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792) 中介绍的搜索顺序  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>动态链接优于静态链接  
 我们建议你在重新发布 Visual C++ 库时避免使用静态链接。 虽然静态链接几乎从未显著提高应用程序性能，但却几乎总是增加服务的成本。 例如，一个应用程序静态链接到因安全性增强而更新的库，则除非应用程序进行重新编译和重新部署，否则不会从中受益。 因此我们建议你将应用程序动态链接到它们所依赖的库，以便在任何部署位置都能更新库。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)   
 [部署示例](../ide/deployment-examples.md)