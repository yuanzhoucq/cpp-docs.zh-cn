---
title: "\"高级\" 属性页 (项目)"
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315526"
---
# <a name="advanced-property-page"></a>"高级" 属性页

Visual Studio 2019 和更高版本中提供了 "高级" 属性页。

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>高级属性

- **目标文件扩展名**

   指定要用于生成输出的文件扩展名。 适用于应用程序的 **.exe** 、适用于静态库的 **.lib**和 dll 的 **.dll** 。

- **清除时要删除的文件扩展名**

   “清理”选项（“生成”菜单）从生成项目的配置的中间目录中删除文件   。 具有此属性指定的扩展名的文件将在运行“清理”或当你执行重新生成时被删除  。 除了中间目录中具有这些扩展名的文件以外，生成系统也将删除任何已知的生成输出，而无论它所在的位置（包括中间输出，如 .obj 文件）。 请注意，你可以指定通配符。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **生成日志文件**

   允许你指定生成项目时创建的日志文件的非默认位置。 默认位置由宏 $(IntDir)$(MSBuildProjectName).log 指定。

   可使用项目宏来更改目录位置。 请参阅[用于生成命令和属性的常见宏](common-macros-for-build-commands-and-properties.md)。

- **首选生成工具体系结构**

   指定是否使用 x86 或 x64 生成工具。

- **使用调试库**

   指定是创建调试版本还是发布版本。

- **启用 Unity (巨型) 生成**

   启用在编译之前将多C++个源文件合并到一个或多个 "unity" 文件中以提高生成性能的生成过程。 与 Unity 游戏引擎无关。

- **MFC 的使用**

   指定 MFC 项目将静态还是动态链接到 MFC DLL。 非 MFC 项目可以选择“使用标准 Windows 库”以链接到使用 MFC 时将包括在内的各种 Win32 库  。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字符集**

   定义应设置 _UNICODE 还是 _MBCS。 在适当的情况下，还会影响链接器入口点。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **全程序优化**

   指定 [/GL](gl-whole-program-optimization.md) 编译器选项和 [/LTCG](ltcg-link-time-code-generation.md) 链接器选项。 默认情况下，此选项对于调试配置是禁用的，对于零售配置是启用的。

- **MSVC 工具集版本**

   指定将用于生成项目的 MSVC 工具集的完整版本。 如果安装了不同版本的工具集, 则可以在此处指定要使用的工具集。

## <a name="ccli-properties"></a>C++/CLI 属性

- **公共语言运行时支持**

   导致要使用 [/clr](clr-common-language-runtime-compilation.md) 编译器选项。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **.NET 目标框架版本**

   在托管项目中指定要面向的 .NET Framework 版本。

- **启用托管增量生成**

   对于托管项目，这可在生成程序集时启用外部可见性的检测。 如果某个托管项目的更改对其他项目不可见，则不重新生成依赖项目。 对于包括托管项目的解决方案，这样可以显著改善其中的生成时间。

::: moniker-end
