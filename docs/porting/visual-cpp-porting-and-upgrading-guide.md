---
title: Visual C++ 移植和升级指南 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 084c689ad7720e36670130d552522aa2f593218e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Visual C++ 移植和升级指南
本主题提供有关升级 Visual c++ 代码的指南。 它包括获取要编译和在新版本的工具上运行的代码，以及利用新语言和 Visual Studio 功能。 本主题还包括有关将原有应用迁移到更现代的平台的信息。  
  
## <a name="reasons-to-upgrade-visual-c-code"></a>升级 Visual C++ 代码的原因  
 应考虑出于以下原因升级你的代码：  
  
-   由于改进了编译器优化，可实现更快的代码。  
  
-   由于编译器本身性能的改进，可实现更快的生成。  
  
-   改进了标准符合性。 现在 Visual C++ 可依照最新的 C++ 标准实现许多功能。  
  
-   更好的安全性。 安全功能，如保护检查。  
  
### <a name="porting-your-code"></a>移植代码  
 升级时，首先考虑应用程序代码和项目。 你的应用程序是使用 Visual Studio 生成的吗？  如果是，确定所涉及的项目。  是否拥有自定义生成脚本？  如果拥有自定义生成脚本，而不是使用 Visual Studio 的生成系统，升级中将需要完成更多的工作，因为无法通过使用 Visual Studio 升级项目文件和生成设置来节省时间。  
  
 Visual Studio 中的生成系统和项目文件格式从 Visual Studio 2008 及之前版本中的 vcbuild 更改为 Visual Studio 2010 及之后版本中的 MSBuild。 如果是从 2010 之前的版本升级，并且具有高度自定义的生成系统，可能不得不完成更多的工作以进行升级。  如果是从 Visual Studio 2010 及之后的版本升级，则你的项目已经在使用 MSBuild 了，所以为应用程序升级项目和生成应该会比较容易。  
  
 如果不使用 Visual Studio 的生成系统，则应考虑升级以使用 MSBuild。 如果升级以使用 MSBuild，可能在以后的升级中会更轻松，使用诸如 Visual Studio Online 等服务将会更容易。 MSBuild 支持 Visual Studio 支持的所有目标平台。  
  
### <a name="porting-visual-studio-projects"></a>移植 Visual Studio 项目  
  要开始升级项目或解决方案，只需在新版本的 Visual Studio 中打开解决方案，然后按提示开始对其进行升级。  升级项目时，你将获取一个升级报告，该报告也将在你的项目文件夹中保存为 UpgradeLog.htm。 该升级报告显示有关升级过程中所遇到的问题的总结和有关所做更改或无法自动解决的问题的一些信息。  
  
1.  项目属性  
  
2.  包含文件  
  
3.  由于编译器符合性的改进或标准中的更改而无法完全编译的代码  
  
4.  依赖于不再可用的 Visual Studio 或 Windows 功能或未包含在 Visual Studio 默认安装中或已从产品中移除的标头文件的代码  
  
5.  由于 API 中的更改（如 API 重命名、函数签名更改或函数弃用）而不再编译的代码  
  
6.  由于诊断中的更改（如警告变为错误）而不再编译的代码  
  
7.  由于库更改导致的链接器错误（尤其是使用 /NODEFAULTLIB 时）。  
  
8.  行为更改所导致的运行时错误或意外结果  
  
9. 由于这些工具中引入的错误而导致的错误。 如果遇到问题，请通过正常支持渠道或通过使用 [Visual Studio 反馈中心](http://connect.microsoft.com/VisualStudio/Feedback)将其报告给 Visual C++ 团队。  
  
 除了由于编译器错误所导致的无法避免的更改，某些更改在升级过程中是可选的，如：  
  
1.  新的警告可能意味着你想要清理你的代码。 具体取决于特定诊断，这可以提高你的代码的可移植性、标准符合性和安全性。  
  
2.  利用添加对未授权代码执行的检查的编译器新功能，如 [/guard:cf（启用流控制保护）](../build/reference/guard-enable-control-flow-guard.md)编译器选项。  
  
3.  你可能想要更新一些代码以使用可简化代码的新语言功能、提高程序的性能，或更新代码以使用现代库并遵循现代标准和最佳做法。  
  
 升级并测试项目后，可能需要考虑进一步改善代码或规划代码的未来方向，或甚至重新考虑项目的体系结构。 它是否会接收进行中的开发工作？ 代码可在其他平台上运行是否重要？  如果是，是哪些平台？  C++ 是充分考虑了可移植性和跨平台开发而设计的标准化语言，但许多 Windows 应用程序的代码在很大程度上依赖于 Windows 平台。 是否想重构代码以分隔出那些更依赖于 Windows 平台的那部分代码？  
  
 你的用户界面呢？  如果你正在使用 MFC，可能会想要更新 UI。  你是否正在使用在 2008 年作为功能包引入的任何更新的 MFC 功能？  如果只是想要让应用获得更新的外观和感觉，而不重写整个应用，则可以考虑使用 MFC 中的功能区 API 或使用 MFC 的一些新功能。  
  
 如果想要为程序提供 XAML 用户界面，但不想创建 UWP 应用，可以将 C# 与 WPF 搭配使用以创建 UI 层，并将标准 C ++ 逻辑重构到 DLL。 在 C++/CLI 中创建互操作性层，以连接 C# 和本机代码。 创建 UWP 应用的另一种方法是使用 [C++/CX](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh699871.aspx) 或 [C++/WinRT](https://github.com/microsoft/cppwinrt)。 在 Windows 10 中，可以使用 [Desktop App Converter](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) 将现有桌面应用程序打包为 UWP 应用，而无需修改任何代码。   
 或者，也许你现在有新的需求，或可以预见到需要面向除 Windows 桌面外的平台，如 Windows Phone 或 Android 设备。 你可以将你的用户界面代码移植到跨平台的 UI 库。 通过这些 UI 框架，可以面向多个设备并仍然使用 Visual Studio 和 Visual Studio 调试器作为开发环境。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|讨论如何使用在早期版本的 Visual C++ 中创建的项目。|  
|[Visual Studio 2017 RC 中 C++ 编译器的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)|从 Visual Studio 2015 到 Visual Studio 2017 的 IDE 和工具更改|  
|[Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)|从 Visual Studio 2015 到 Visual Studio 2017 的标准符合性改进|  
|[Visual C++ 更改历史记录（2003 - 2015）](visual-cpp-change-history-2003-2015.md)|导致代码可能需要更改的 Visual C++ 库和生成工具中的所有更改的列表（从 Visual Studio 2003 到 Visual Studio 2015）。|  
|[Visual C++ 新增功能（2003 - 2015）](visual-cpp-what-s-new-2003-through-2015.md)|从 Visual Studio 2003 到 Visual Studio 2015 的所有 Visual C++“新增功能”信息。|  
|[移植第三方库](porting-third-party-libraries.md)|如何使用 **vcpkg** 命令行工具将较旧的开源库移植到使用较新的 Visual C++ 工具集编译的版本。|  
|[移植和升级：示例和案例研究](porting-and-upgrading-examples-and-case-studies.md)|本部分中，我们移植和升级了多个示例和应用程序并讨论了体验和结果。 你可能会发现阅读这些内容会使你了解移植和升级过程中所涉及的内容。 在整个过程中，我们讨论了升级所用的提示和技巧，并演示如何修复特定错误。|  
|[移植到通用 Windows 平台](porting-to-the-universal-windows-platform-cpp.md)|包含有关移植代码到 Windows 10 的信息|  
|[Visual C++ 简介（针对 UNIX 用户）](introduction-to-visual-cpp-for-unix-users.md)|为不熟悉 Visual C++ 并想要有效率的使用它的 UNIX 用户提供信息。|  
|[从 UNIX 移植到 Win32](porting-from-unix-to-win32.md)|讨论用于将 UNIX 应用程序迁移到 Windows 的选项。|  
|[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)|详细演示如何升级 C++ 语法的托管扩展来使用新的语法。 有关详细信息，请参阅[运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。|  
  
## <a name="see-also"></a>请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)
