---
title: 选择部署方法 |Microsoft 文档
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="choosing-a-deployment-method"></a>选择部署方法
除非你的 Visual c + + 应用程序是独立的并且可以通过使用复制命令部署，否则我们建议你使用 Windows Installer 进行部署。 Windows Installer 支持安装、修复和卸载，还支持应用程序文件、依赖项和注册表项的原子更新。  
  
> [!NOTE]
>  尽管[ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) Visual c + + 本机应用程序的部署是无法在 Visual Studio 中，它需要额外的步骤。 有关详细信息，请参阅 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++ 库是共享的 DLL  
 由于 Visual C++ 库由 Visual Studio 安装程序安装在 %windir%\system32\ 目录中，所以当你开发依赖这些库的 Visual C++ 应用程序时，它会按预期运行。 但是，若要将应用程序部署到可能没有 Visual Studio 的计算机，我们建议你确保库与应用程序一起安装在这些计算机中。  
  
## <a name="redistributing-visual-c-libraries"></a>重新发布 Visual C++ 库  
 在你的部署中，可以重新发布获得重新发布许可的任何版本的 Visual C++ 库。 以下是三种部署方法：  
  
-   使用集中部署可再发行组件包，从而安装 Visual c + + 库作为共享 Dll 中 %windir%\system32\\。 （安装到该文件夹中需要管理员权限。）你可以创建一个脚本或安装程序，以便在目标计算机上安装应用程序之前运行可再发行组件包。 可再发行组件包可用于 x86、x64 和 ARM 平台（VCRedist_x86.exe、VCRedist_x64.exe 或 VCRedist_arm.exe）。 Visual Studio 在 %programfiles (x86) %\Microsoft Visual Studio 中包含这些包`version`\VC\Redist\\`locale ID`\\。 你也可以下载它们从[Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793)。 (在下载中心使用搜索框来搜索"Visual c + + 可再发行组件包*Visual Studio 版本和更新*"与匹配你的应用程序。 例如，如果你使用 Visual Studio 2015 update 3 都生成应用程序，然后搜索"Visual c + + 可再发行组件包 2015 update 3"。)有关如何使用可再发行组件包的信息，请参阅[演练： 部署 Visual c + + 应用程序通过使用 Visual c + + 可再发行组件包](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
-   集中部署使用合并模块，其中每个会安装特定的 Visual c + + 库作为共享 DLL 中 %windir%\system32\\。 （安装到该文件夹中需要管理员权限。）合并模块将成为你应用程序的 .msi 安装程序文件的一部分。 Visual c + + 可再发行合并模块包含在 Visual Studio 的 \Program Files (x86) \common 模块\\。 有关详细信息，请参阅[通过使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)。  
  
-   本地部署，从你的 Visual Studio 安装复制特定的 Visual c + + Dll-一般位于 \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and在应用程序可执行文件所在的文件夹中的目标计算机上安装它们。 你可以使用该部署方法启用无管理员权限的用户的安装，或可从网络共享运行的应用程序的安装。  
  
 如果部署使用可再发行合并模块，并且安装程序运行不具有管理权限的用户，未安装 Visual c + + Dll 和应用程序将不会运行。 另外，通过允许按用户安装的合并模块生成的应用程序安装程序会将库安装在影响所有系统用户的共享位置中。 可以使用本地部署在特定用户的应用程序的目录中安装所需的 Visual c + + Dll，而不影响其他用户也需要管理员权限。 由于这可能会造成可服务性问题，我们不建议本地部署的 Visual c + + 可再发行 Dll。  
  
 Visual C++ 库的错误部署可能导致执行依赖于这些库的应用程序时出现运行时错误。 当操作系统加载应用程序时，它将使用中所述的搜索顺序[LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>动态链接优于静态链接  
 我们建议你避免静态链接，当你重新分发 Visual c + + 库时。 虽然静态链接几乎从未显著提高应用程序性能，但却几乎总是增加服务的成本。 例如，一个应用程序静态链接到因安全性增强而更新的库，则除非应用程序进行重新编译和重新部署，否则不会从中受益。 因此我们建议你将应用程序动态链接到它们所依赖的库，以便在任何部署位置都能更新库。  
  
## <a name="see-also"></a>请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)   
 [部署示例](../ide/deployment-examples.md)