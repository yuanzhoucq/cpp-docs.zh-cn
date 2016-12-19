---
title: "Visual C++ 移植和升级指南 | Microsoft Docs"
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
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 移植和升级指南
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题提供有关升级 Visual c\+\+ 代码的指南。  它包括获取要编译和在新版本的工具上运行的代码，以及利用新语言和 Visual Studio 功能。  本主题还包括有关将原有应用迁移到更现代的平台的信息。  
  
## 升级 Visual C\+\+ 代码的原因  
 应考虑出于以下原因升级你的代码：  
  
-   由于改进了编译器优化，可实现更快的代码。  
  
-   由于编译器本身性能的改进，可实现更快的生成。  
  
-   语言功能。  现在 Visual C\+\+ 可从更新的 C\+\+ 标准实现许多功能。  
  
-   更好的安全性。  安全功能，如保护检查。  
  
### 移植代码  
 升级时，首先考虑应用程序代码和项目。  你的应用程序是使用 Visual Studio 生成的吗？  如果是，确定所涉及的项目。  是否拥有自定义生成脚本？  如果拥有自定义生成脚本，而不是使用 Visual Studio 的生成系统，升级中将需要完成更多的工作，因为无法通过使用 Visual Studio 升级项目文件和生成设置来节省时间。  
  
 Visual Studio 中的生成系统和项目文件格式从 Visual Studio 2008 及之前版本中的 vcbuild 更改为 Visual Studio 2010 及之后版本中的 MSBuild。  如果是从 2010 之前的版本升级，并且具有高度自定义的生成系统，可能不得不完成更多的工作以进行升级。  如果是从 Visual Studio 2010 及之后的版本升级，则你的项目已经在使用 MSBuild 了，所以为应用程序升级项目和生成应该会比较容易。  
  
 如果不使用 Visual Studio 的生成系统，则应考虑升级以使用 MSBuild。  如果升级以使用 MSBuild，可能在以后的升级中会更轻松，使用诸如 Visual Studio Online 等服务将会更容易。  MSBuild 支持 Visual Studio 支持的所有目标平台。  
  
### 移植 Visual Studio 项目  
 对于更大型的项目，可能希望一次只升级一个 Visual Studio 版本，因为不这样做就很难知道哪个版本引入了影响了你代码的特定重大更改。  
  
 要开始升级项目或解决方案，只需在新版本的 Visual Studio 中打开解决方案，然后按提示开始对其进行升级。  升级项目时，你将获取一个升级报告，该报告也将在你的项目文件夹中保存为 UpgradeLog.htm。  该升级报告显示有关升级过程中所遇到的问题的总结和有关所做更改或无法自动解决的问题的一些信息。  
  
1.  项目属性  
  
2.  包含文件  
  
3.  由于编译器一致性更改而无法完全编译的代码  
  
4.  依赖于不再可用的 Visual Studio 或 Windows 功能或未包含在 Visual Studio 默认安装中或已从产品中移除的标头文件的代码  
  
5.  由于 API 中的更改（如 API 重命名、函数签名更改或函数弃用）而不再编译的代码  
  
6.  由于诊断中的更改（如警告变为错误）而不再编译的代码  
  
7.  由于库更改导致的链接器错误（尤其是使用 \/NODEFAULTLIB 时）。  
  
8.  行为更改所导致的运行时错误或意外结果  
  
9. 由于这些工具中引入的错误而导致的错误。  如果遇到问题，请通过正常支持渠道或通过使用 [Visual Studio 反馈中心](http://connect.microsoft.com/VisualStudio/Feedback)将其报告给 Visual C\+\+ 团队。  
  
 除了由于编译器错误所导致的无法避免的更改，某些更改在升级过程中是可选的，如：  
  
1.  新的警告可能意味着你想要清理你的代码。  具体取决于特定诊断，这可以提高你的代码的可移植性、标准一致性和安全性。  
  
2.  你可能想要利用编译器的新功能，如 [\/guard:cf（启用流控制保护）](../build/reference/guard-enable-control-flow-guard.md)编译器选项，可添加针对未经授权的代码执行的检查。  
  
3.  你可能想要更新一些代码以使用可简化代码的新语言功能、提高程序的性能，或更新代码以使用现代库并遵循现代标准和最佳做法。  
  
 一旦升级了项目（并对其进行了测试），你可能还想考虑进一步改善代码或规划代码的未来方向，或甚至重新考虑项目的体系结构。  代码可在其他平台上运行是否重要？  如果是，是哪些平台？  C\+\+ 是充分考虑了可移植性和跨平台开发而设计的标准化语言，但许多 Windows 应用程序的代码在很大程度上依赖于 Windows 平台。  是否想重构代码以分隔出那些更依赖于 Windows 平台的那部分代码？  
  
 你的用户界面呢？  如果你正在使用 MFC，可能会想要更新 UI。  你是否正在使用在 2008 年作为功能包引入的任何更新的 MFC 功能？  如果只是想要让应用获得更新的外观和感觉，而不重写整个应用，则可以考虑使用 MFC 中的功能区 API 或使用 MFC 的一些新功能。  
  
 要添加新的 Windows 桌面用户界面，可以使用 C\+\+\/CX（组件扩展）或添加 C\# 中的托管代码和 C\+\+\/CLI 中的互操作性层，将 C\# 与你的本机代码相连。  
  
 或者，也许你现在有新的要求，或可以预见到需要面向除 Windows 桌面外的平台，如 Windows Phone 或 Android 设备。  你可以将你的用户界面代码移植到跨平台的 UI 库。  使用这些 UI 框架，你可以面向多个设备并仍然使用 Visual Studio 和 Visual Studio 调试器作为开发环境。  
  
## 相关主题  
  
|标题|描述|  
|--------|--------|  
|[从 Visual C\+\+ 早期版本升级项目](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)|讨论如何使用在早期版本的 Visual C\+\+ 中创建的项目。|  
|[Visual C\+\+ 2015 中的重大更改](../porting/visual-cpp-change-history-2003-20151.md)|代码需要更改的 Visual C\+\+ 库和生成工具中的更改列表。|  
|[迁移和升级：示例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)|本部分中，我们移植和升级了多个示例和应用程序并讨论了体验和结果。  你可能会发现阅读这些内容会使你了解移植和升级过程中所涉及的内容。  在整个过程中，我们讨论了升级所用的提示和技巧，并演示如何修复特定错误。|  
|[迁移到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)|包含有关移植代码到 Windows 10 的信息|  
|[Visual C\+\+ 简介（针对 UNIX 用户）](../porting/introduction-to-visual-cpp-for-unix-users.md)|为不熟悉 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 并想要有效率的使用它的 UNIX 用户提供信息。|  
|[从 UNIX 到 Win32 的迁移](../porting/porting-from-unix-to-win32.md)|讨论用于将 UNIX 应用程序迁移到 Windows 的选项。|  
|[C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)|详细演示如何升级 C\+\+ 语法的托管扩展来使用新的语法。  有关详细信息，请参阅[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。|  
  
## 请参阅  
 [Visual C\+\+ 2015 中的重大更改](../porting/visual-cpp-change-history-2003-20151.md)