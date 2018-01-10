---
title: "链接器工具错误 LNK1104 |Microsoft 文档"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1104
dev_langs: C++
helpviewer_keywords: LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c91853fe3310d8e577ac884545f86d1f4e1d4521
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104

> 无法打开文件*filename*

链接器无法打开指定的文件。 此问题的最常见原因是，该文件正在使用或另一个进程锁定、 不存在，无法找到链接器搜索时，目录之一中或你可能没有足够的权限访问该文件。 较不常见的是，你可能已用完磁盘空间，该文件可能太大，或文件的路径可能太长。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

链接器尝试打开以进行读取或写入的文件时，可以出现此错误。 若要缩小可能的原因，请首先检查哪种文件，并使用下列部分来帮助识别和解决特定问题。

### <a name="cannot-open-your-app-or-its-pdb-file"></a>无法打开您的应用程序或其的.pdb 文件

如果文件名是可执行文件生成项目，或一个关联的.pdb 文件，最常见原因是当您尝试重新生成它，或在调试器中加载到你的应用程序已在运行。 若要解决此问题，请停止该程序，并将其从调试器卸载之前再次生成。 如果在另一个程序中，打开应用程序 （如资源编辑器），将其关闭。 在极端情况下，你可能需要使用任务管理器终止进程，或停止并重新启动 Visual Studio。

防病毒程序通常暂时块访问新创建的文件，尤其是.exe 和.dll 可执行文件。 若要解决此问题，请尝试从防病毒扫描程序中排除项目生成目录。

### <a name="cannot-open-a-microsoft-library-file"></a>无法打开 Microsoft 库文件

如果无法打开该文件是 kernel32.lib，例如由 Microsoft 提供的标准库文件的一个可能具有项目配置错误或安装错误。 验证是否已安装 Windows SDK，如果你的项目需要 MFC 等其他 Microsoft 库，并确保 Visual Studio 安装程序也已安装 MFC 组件。 你可以运行安装程序以在任何时候添加可选组件。 有关详细信息，请参阅[修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 在安装程序中使用的各个组件选项卡选择特定的库和 Sdk。

如果你正在生成使用较旧版本的 Visual Studio 创建的项目，，系统可能未安装的平台工具集和该版本的库。 如果已进行版本管理的库名称，例如 msvcr100.lib，会出现该错误消息是可能的原因。 若要解决此问题，您具有两个选项： 你可以升级项目以使用你已安装的当前平台工具集，或者可以安装的较旧的工具集和生成项目保持不变。 有关详细信息，请参阅[从早期版本的 Visual c + + 升级项目](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用本机多目标在 Visual Studio 中生成旧项目](../../porting/use-native-multi-targeting.md)。

如果你看到此错误，生成新的目标平台或配置时，可能不会安装该项目配置或平台工具集的库。 验证**平台工具集**和**Windows SDK 版本**中指定[常规属性页](../../ide/general-property-page-project.md)安装为你的项目，并确认所需库位于**库目录**中指定[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)的配置设置。 可以单独设置调试以及零售配置，以及 32 位和 64 位配置，因此如果一个 build 的工作原理，但另一个会导致错误，请确保设置是否正确并为安装所需的工具和库每个生成的配置。

如果使用 Visual Studio IDE 生成项目从另一台计算机复制的则库的安装位置可能不同。 检查**库目录**属性[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)项目和根据需要进行更新。 若要查看和编辑在 IDE 中设置的当前库路径，选择的下拉列表控件**库目录**属性，然后选择**编辑**。 **计算值**部分**库目录**对话框列出了当前搜索库文件的路径。

指向 Windows SDK 的路径已过期时，也可能发生此错误。 如果已安装的版本比你的 Visual Studio 版本新的 Windows sdk，请确保中指定的路径[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)更新以匹配新的 SDK。 如果你使用开发人员命令提示，请确保初始化环境变量的批处理文件，将更新为新的 SDK 路径。 可以通过使用 Visual Studio 安装程序安装更新的 Sdk 避免此问题。

### <a name="cannot-open-a-third-party-library-file"></a>无法打开第三方库文件

有几个此问题的常见原因：

- 库文件的路径可能不正确，或者你可能没有指定它到链接器。

- 你可以已经安装 32 位版本的库中，但你在构建供 64 位，反之亦然。

- 库可能存在未安装其他库依赖关系。

若要解决路径问题，请验证 LIB 环境变量已设置且包含库使用，为你生成每个配置的所有目录。 在 IDE 中，通过设置 LIB 变量**库目录**属性[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)。 请确保为你生成每个配置在这里，列出包含所需的库的所有目录。

如果你需要提供库目录可重写的标准库目录，则可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项在命令行中，或 IDE 中，你可以使用**附加库目录**中的属性**配置属性 > 链接器 > 常规**为你的项目属性页。

请确保已安装每个版本的生成的配置所需的库。 请考虑使用[vcpkg](../../vcpkg.md)包管理实用工具来自动执行的安装和许多常见的库的安装程序。 如果可能，最好生成你自己的第三方库的副本，因此你将确保所有本地依赖这些库要求，并为你的项目相同的配置生成它们。

### <a name="cannot-open-a-file-built-by-your-project"></a>无法打开项目生成的文件

你可能会看到此错误，如果该文件*filename*生成的解决方案，但尚不存在时链接器尝试访问它。 这可能发生在一个项目依赖于另一个项目，但不是按正确的顺序生成项目时。 若要解决此问题，请确保你项目的引用设置中的项目中使用该文件，因此需要提供之前生成缺少的文件。 有关详细信息，请参阅[Visual c + + 项目中添加引用](../../ide/adding-references-in-visual-cpp-projects.md)和[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。

### <a name="cannot-open-file-cprogramobj"></a>无法打开文件 c:\\Program.obj

如果你看到此错误或类似的错误涉及你驱动器的根目录中的意外的.obj 文件，该问题几乎可以肯定是不包装用双引号括起来的库路径。

若要解决此问题的命令行生成，请检查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项参数、 在 LIB 环境变量中，指定的路径和命令行上指定的路径并确保使用双引号解决任何路径这包括空格。

若要在 IDE 中解决此问题，请检查**库目录**属性[配置属性 > VC + + 目录](../../ide/vcpp-directories-property-page.md)属性页中，**附加库目录**中的属性**配置属性 > 链接器 > 常规**属性页中，与**附加依赖项**中的属性**配置属性 > 链接器 > 输入**为你的项目属性页。 请确保包含所需的库的所有目录路径都包装在双引号中，如有必要。

### <a name="other-common-issues"></a>其他常见的问题

当库文件名或路径指定到链接器命令行上或在时会出现此错误[#pragma 注释 （"library_name"中的 lib）](../../preprocessor/comment-c-cpp.md)指令不正确，或者路径具有无效的驱动器规范。 检查拼写和文件扩展名，并验证该文件存在在指定的位置。

另一个程序可能已打开该文件，链接器无法向其写入。 防病毒程序通常暂时阻止对新创建的文件的访问。 若要解决此问题，请尝试从防病毒扫描程序中排除项目生成目录。

如果你使用的并行生成选项，则可能 Visual Studio 已锁定另一个线程上的文件。 要解决此问题，请验证未生成的同一个代码对象或库在多个项目中，并且你使用的生成依赖关系或项目引用来选取你的项目中生成的二进制文件。

当指定在各个库**附加依赖项**属性直接，用空格分隔库名称、 不逗号或分号。 如果你使用**编辑**菜单项以打开**附加依赖项**对话框中，使用换行符分隔的名称，而不是逗号、 分号或空格。 指定库路径中的时也使用换行符**库目录**和**附加库目录**对话框。

你可能会看到此错误时的路径*filename*超过 260 个字符。 更改名称或重新排列你的目录结构，如果需要缩短对所需文件的路径。

因为该文件太大，可能出现此错误。 库或对象的文件超过千兆字节的大小可能在 32 位链接的情况下会导致问题。 此问题的可能解决方法是使用 64 位工具集。 有关如何执行此操作在命令行的详细信息，请参阅[如何： 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 有关如何执行此操作在 IDE 中的信息，请参阅[与 64 位编译器和工具使用 MSBuild](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此堆栈溢出文章：[如何使 Visual Studio 中使用本机 amd64 工具链](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果你有没有足够的文件访问权限，可能出现此错误*filename*。 如果你使用的普通用户帐户和尝试访问受保护的系统目录中的库文件或使用其他具有其原始的权限的用户从复制的文件会发生此设置。 若要解决此问题，请将文件移动到可写的项目目录中。 如果该文件可写目录中，但具有访问权限，你可以使用管理员命令提示符并运行 takeown.exe 命令，以获得的文件的所有权。

当你没有足够的磁盘空间，可以出现错误。 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，一个非常大的链接可以消耗或片段的可用磁盘空间。 请考虑使用[/OPT （优化）](../../build/reference/opt-optimizations.md)选项; 不采取可传递的 COMDAT 消除读取所有对象文件多次。

如果*filename*名为 LNK*nnn*生成链接器为临时文件的文件名时，可能不存在 TMP 环境变量中指定的目录，或多个可能为 TMP 环境变量指定目录。 只能将一个目录路径应为 TMP 环境变量指定。
