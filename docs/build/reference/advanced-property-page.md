---
title: 高级属性页（项目）
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328422"
---
# <a name="advanced-property-page"></a>高级属性页

高级属性页面在 Visual Studio 2019 及更高版本提供。

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>高级属性

- **目标文件扩展名**

   指定要用于生成输出的文件扩展名。 默认为 **.exe**的应用程序，静态库的 **.lib**和 DLL 的 **.dll。**

- **清除时要删除的扩展名**

   “清理”选项（“生成”菜单）从生成项目的配置的中间目录中删除文件********。 具有此属性指定的扩展名的文件将在运行“清理”或当你执行重新生成时被删除****。 除了中间目录中具有这些扩展名的文件以外，生成系统也将删除任何已知的生成输出，而无论它所在的位置（包括中间输出，如 .obj 文件）。 请注意，你可以指定通配符。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **生成日志文件**

   允许你指定生成项目时创建的日志文件的非默认位置。 默认位置由宏 $(IntDir)$(MSBuildProjectName).log 指定。

   可使用项目宏来更改目录位置。 有关[生成命令和属性，请参阅通用宏](common-macros-for-build-commands-and-properties.md)。

- **首选构建工具体系结构**

   指定是使用 x86 还是 x64 生成工具。

- **使用调试库**

   指定是创建 DEBUG 还是"释放"生成。

- **启用统一 （JUMBO） 生成**

   启用生成过程，其中许多C++源文件在编译前合并到一个或多个"统一"文件中，以提高生成性能。 与 Unity 游戏引擎无关。

- **MFC 的使用**

   指定 MFC 项目将静态还是动态链接到 MFC DLL。 非 MFC 项目可以选择“使用标准 Windows 库”以链接到使用 MFC 时将包括在内的各种 Win32 库****。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字符集**

   定义应设置 _UNICODE 还是 _MBCS。 在适当的情况下，还会影响链接器入口点。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **全程序优化**

   指定 [/GL](gl-whole-program-optimization.md) 编译器选项和 [/LTCG](ltcg-link-time-code-generation.md) 链接器选项。 默认情况下，此选项对于调试配置是禁用的，对于零售配置是启用的。

- **MSVC 工具集版本**

   指定将用于生成项目的 MSVC 工具集的完整版本。 如果安装了工具集的各种更新和预览版本，则可以在此处指定要使用的版本。

## <a name="ccli-properties"></a>C++/CLI 属性

- **公共语言运行时支持**

   导致要使用 [/clr](clr-common-language-runtime-compilation.md) 编译器选项。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **.NET 目标框架版本**

   在托管项目中指定要面向的 .NET Framework 版本。

- **启用托管增量生成**

   对于托管项目，这可在生成程序集时启用外部可见性的检测。 如果某个托管项目的更改对其他项目不可见，则不重新生成依赖项目。 对于包括托管项目的解决方案，这样可以显著改善其中的生成时间。

::: moniker-end
