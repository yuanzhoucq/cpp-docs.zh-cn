---
title: 链接器工具错误 LNK1104
ms.date: 05/17/2017
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: fcd3c06ae2db5c43aacbf781800870a83d2d77c1
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451133"
---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104

> 无法打开文件*文件名*

链接器无法打开指定的文件。 此问题的最常见原因是，该文件正在使用中或另一个进程锁定、 不存在，不能在链接器搜索的目录之一中找到或可能没有足够的权限访问该文件。 不太常见的是，您可能已用完磁盘空间，该文件可能太大，或文件的路径可能太长。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

链接器尝试打开的文件进行读取或写入时，会出现此错误。 若要缩小可能的原因，首先检查什么类型的文件，并使用下列部分来帮助识别和解决特定问题。

### <a name="cannot-open-your-app-or-its-pdb-file"></a>无法打开您的应用程序或其.pdb 文件

如果文件名为可执行文件生成项目，或一个关联的.pdb 文件，最常见原因是尝试重新生成它，或在调试程序中加载时，你的应用程序已在运行。 若要解决此问题，请停止该程序并将其从调试程序卸载之前再次生成。 如果应用是在另一个程序中，打开资源编辑器，如将其关闭。 在极端情况下，可能需要使用任务管理器终止该进程，或停止并重新启动 Visual Studio。

防病毒程序通常暂时阻止访问到新创建的文件，尤其是.exe 和.dll 可执行文件。 若要解决此问题，请尝试从防病毒扫描程序排除项目生成目录。

### <a name="cannot-open-a-microsoft-library-file"></a>无法打开 Microsoft 库文件

如果无法打开该文件是 Microsoft 提供的例如 kernel32.lib，标准库文件之一可能会具有项目配置错误或安装错误。 验证是否已安装 Windows SDK，如果你的项目需要 MFC 等其他 Microsoft 库，请确保 Visual Studio 安装程序还已安装 MFC 组件。 你可以运行安装程序再次以随时添加可选组件。 有关详细信息，请参阅[修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 在安装程序中使用单个组件选项卡选择特定的库和 Sdk。

如果您正在构建使用较旧版本的 Visual Studio 创建的项目，平台工具集和该版本的库可能不会安装。 如果为一个带有版本的库名称，例如 msvcr100.lib，出现错误消息这可能是原因。 若要解决此问题，有两个选项： 则可以升级项目以使用当前的平台工具集，它们已安装，也可以安装较旧的工具集并生成项目保持不变。 有关详细信息，请参阅[从早期版本 Visual 升级项目C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)并[使用的本机多目标在 Visual Studio 中来生成旧项目](../../porting/use-native-multi-targeting.md)。

如果在生成新的目标平台或配置时看到此错误，可能未安装该项目配置或平台工具集的库。 确认**平台工具集**并**Windows SDK 版本**中指定[常规属性页](../../build/reference/general-property-page-project.md)安装为你的项目，并验证所需库位于**库目录**中指定[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)的配置设置。 有单独的调试设置和零售配置，以及 32 位和 64 位配置，因此如果一个生成的工作原理，但另一个将导致错误，请确保设置正确无误，并且为安装所需的工具和库每个生成的配置。

如果使用 Visual Studio IDE 生成项目从另一台计算机复制，库的安装位置可能不同。 检查**库目录**上的属性[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)项目和根据需要进行更新。 若要查看和编辑在 IDE 中设置的当前库路径，选择的下拉列表控件**库目录**属性，然后选择**编辑**。 **计算值**一部分**库目录**对话框列出了当前搜索库文件的路径。

Windows SDK 的路径已过期时，也可以发生此错误。 如果已安装的版本比你的 Visual Studio 版本的 Windows sdk，请确保在指定的路径[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)更新以匹配新的 SDK。 如果使用开发人员命令提示，请确保初始化环境变量的批处理文件已更新为新的 SDK 路径。 通过使用 Visual Studio 安装程序来安装更新的 Sdk，可以避免此问题。

### <a name="cannot-open-a-third-party-library-file"></a>无法打开第三方库文件

有多个此问题的常见原因：

- 库文件的路径可能不正确，或者您可能没有指定该链接器。

- 您可能已安装的 32 位版本的库，但你正在为 64 位或进行相反转换创建。

- 库可能依赖于未安装其他库。

若要解决一个路径问题，请验证 LIB 环境变量被设置，并且包含使用，为每一种配置生成的库的所有目录。 在 IDE 中，通过设置 LIB 变量**库目录**上的属性[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)。 请确保包含所需的库的所有目录这里都列出了为每个生成的配置。

如果你需要提供库目录重写的标准库目录，可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项在命令行或 IDE 中，可以使用**附加库目录**中的属性**配置属性 > 链接器 > 常规**为你的项目属性页。

请确保已安装每个版本的生成的配置所需的库。 请考虑使用[vcpkg](../../vcpkg.md)包管理实用程序来自动执行的安装和设置适用于许多常见的库。 如果可能，最好生成你自己的第三方库的副本，以确保具有所有本地依赖项，这些库要求，并在生成的与项目相同的配置。

### <a name="cannot-open-a-file-built-by-your-project"></a>无法打开由项目生成的文件

您可能会看到此错误，如果该文件*文件名*生成的解决方案，但尚不存在时链接器尝试访问它。 当一个项目依赖于另一个项目，但不是正确的顺序生成项目时，可以发生这种情况。 若要解决此问题，请确保你的项目引用中使用该文件，因此需要之前生成缺少的文件的项目设置。 有关详细信息，请参阅[在 Visual Studio 中添加引用C++项目](../../build/adding-references-in-visual-cpp-projects.md)并[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。

### <a name="cannot-open-file-cprogramobj"></a>无法打开文件 c:\\Program.obj

如果看到此错误或类似的错误涉及您的根目录中的意外的.obj 文件，但问题是驱动器的几乎可以肯定不包装在双引号内的库路径。

若要解决此问题的命令行生成，请检查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项参数、 LIB 环境变量中指定的路径和命令行上指定的路径，请确保使用双引号围绕任何路径包含空格。

若要在 IDE 中解决此问题，请检查**库目录**上的属性[配置属性 > VC + + 目录](../../build/reference/vcpp-directories-property-page.md)属性页中，**附加库目录**中的属性**配置属性 > 链接器 > 常规**属性页中，和**附加依赖项**中的属性**配置属性 > 链接器 > 输入**为你的项目属性页。 请确保包含所需的库的目录路径都包装在双引号中，如有必要。

### <a name="other-common-issues"></a>其他常见的问题

链接器命令行上或在指定库文件名或路径时，会出现此错误[#pragma 注释 （lib，"library_name"）](../../preprocessor/comment-c-cpp.md)指令不正确，或者该路径具有无效的驱动器规范。 检查你的拼写和文件扩展名，并验证该文件存在于指定位置。

另一个程序可能已打开该文件，链接器无法向其写入。 防病毒程序通常暂时阻止对新创建的文件的访问。 若要解决此问题，请尝试从防病毒扫描程序排除项目生成目录。

如果使用并行生成选项，就可以在 Visual Studio 已锁定另一个线程上的文件。 若要解决此问题，请验证不生成相同的代码对象或多个项目中的库，你将生成依赖项或项目的引用来选取你的项目中生成的二进制文件。

指定在各个库时**附加依赖项**属性直接使用空格来分隔库名称、 不逗号或分号。 如果您使用**编辑**菜单项以打开**附加依赖项**对话框中，使用换行符分隔的名称，而不是逗号、 分号或空格。 指定库路径中的时也使用换行符**库目录**并**附加库目录**对话框。

您可能会看到此错误时的路径*文件名*扩展到超过 260 个字符。 更改名称或重新排列您的目录结构，如果需要缩短所需的文件的路径。

由于文件太大，可能出现此错误。 库或对象文件的详细信息不是千兆字节的大小可能会导致 32 位链接器出现问题。 可能的修复此问题是使用 64 位工具集。 有关如何执行此操作在命令行的详细信息，请参阅[如何：启用 64 位视觉对象C++命令行上的工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 有关如何执行此操作在 IDE 中的信息，请参阅[使用带有 64 位编译器和工具的 MSBuild](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此堆栈溢出文章：[如何让 Visual Studio 使用本机 amd64 工具链](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果您有没有足够的文件访问权限，可能出现此错误*文件名*。 如果您使用普通用户帐户并尝试访问受保护的系统目录中的库文件或使用具有其原始权限的其他用户从复制的文件发生这种情况设置。 若要解决此问题，请将文件移动到可写的项目目录。 如果该文件可写目录中，但具有访问权限，可以使用管理员命令提示符并运行 takeown.exe 命令，以获得文件的所有权。

没有足够的磁盘空间时，可能出现此错误。 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，一个非常大的链接可以消耗或片段的可用磁盘空间。 请考虑使用[/OPT （优化）](../../build/reference/opt-optimizations.md)选项; 执行可传递的 COMDAT 消除读取所有对象文件多次。

如果*文件名*名为 LNK*nnn*，这是一个临时文件的链接器生成的文件名、 TMP 环境变量中指定的目录可能不存在，或可能是多个目录为 TMP 环境变量指定。 只能将一个目录路径应为 TMP 环境变量指定。
