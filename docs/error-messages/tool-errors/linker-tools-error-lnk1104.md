---
title: 链接器工具错误 LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808841"
---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104

> 无法打开文件 "*filename*"

链接器无法打开指定的文件。 此问题最常见的原因是该文件正在使用中或被另一个进程锁定。 此文件也可能不存在，或者无法在链接器搜索的目录之一中找到该文件。 或者您可能没有足够的权限访问该文件。 通常，磁盘空间可能已用完，文件可能太大，或者文件的路径可能太长。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方法

当链接器尝试打开文件进行读取或写入时，可能会发生此错误。 若要缩小可能的原因，请首先检查文件的类型。 然后，使用下列部分来帮助确定并解决特定问题。

### <a name="cant-open-your-app-or-its-pdb-file"></a>无法打开应用或其 .pdb 文件

如果 filename 是您的项目生成的可执行文件或关联的 .pdb 文件，最常见的原因是您的应用程序在您尝试重新生成它或已加载到调试器中时已在运行。 若要解决此问题，请先停止程序并从调试器中卸载它，然后再重新生成它。 如果应用已在其他程序（如资源编辑器）中打开，请将其关闭。 在极端情况下，可能需要使用任务管理器终止进程，或停止并重新启动 Visual Studio。

防病毒程序通常会暂时阻止对新创建的文件（尤其是 .exe 和 .dll 可执行文件）的访问。 若要解决此问题，请尝试从防病毒扫描程序中排除你的项目生成目录。

### <a name="cant-open-a-microsoft-library-file"></a>无法打开 Microsoft 库文件

如果无法打开的文件是 Microsoft 提供的标准库文件之一（如 kernel32.dll），则可能会出现项目配置错误或安装错误。 验证是否已安装 Windows SDK，并且如果你的项目需要其他 Microsoft 库（如 MFC），请确保 Visual Studio 安装程序也安装了 MFC 组件。 你可以随时运行安装程序来添加可选组件。 有关详细信息，请参阅[修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安装程序中的 "单个组件" 选项卡选择特定的库和 Sdk。

对于通用 Windows （UWP）应用或组件，没有 Spectre 的库。 如果错误报告提到*vccorlib.h*文件，则可能已在 UWP 项目中启用了[/Qspectre](../../build/reference/qspectre.md) 。 禁用 **/Qspectre**编译器选项以解决此问题。 在 Visual Studio 中，更改 "项目**属性页**" 对话框的 " **CC++/**  > **代码生成**" 页中的**Spectre 缓解**属性。

如果要生成的项目是使用较旧版本的 Visual Studio 创建的，则可能不会安装该版本的平台工具集和库。 如果错误消息针对版本控制的库名称（如 msvcr100.dll) 而）出现，则这可能是原因。 若要解决此问题，你可以使用两个选项：可以升级项目以使用已安装的当前平台工具集，也可以安装旧版工具集并不更改项目。 有关详细信息，请参阅[从C++ visual Studio 的早期版本升级项目](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用 visual Studio 中的本机多目标来生成旧项目](../../porting/use-native-multi-targeting.md)。

如果在为新的目标平台或配置生成时看到此错误，则可能不会安装该项目配置的库或平台工具集。 验证是否已安装在项目的 "[常规" 属性页](../../build/reference/general-property-page-project.md)中指定的**平台工具集**和**Windows SDK 版本**，并验证所**需的库**在配置设置的 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)。 有单独的设置用于调试和零售配置，以及32位和64位配置，因此，如果一个生成工作而另一个生成发生错误，请确保设置正确，并为每个生成的配置。

如果使用 Visual Studio IDE 生成从另一台计算机复制的项目，则库的安装位置可能会不同。 检查项目的 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)上的 "**库目录**" 属性，并根据需要进行更新。 若要查看和编辑 IDE 中设置的当前库路径，请选择 "**库目录**" 属性的下拉控件，然后选择 "**编辑**"。 "**库目录**" 对话框的 "**计算值**" 部分列出了为库文件搜索的当前路径。

如果 Windows SDK 的路径过期，也会发生此错误。 如果你安装了比你的 Visual Studio 版本新的 Windows SDK 版本，请确保更新了 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)中指定的路径，以匹配新的 SDK。 如果使用开发人员命令提示，请确保为新的 SDK 路径更新初始化环境变量的批处理文件。 可以通过使用 Visual Studio 安装程序安装更新的 Sdk 来避免此问题。

### <a name="cannot-open-a-third-party-library-file"></a>无法打开第三方库文件

此问题有几个常见的原因：

- 库文件的路径可能不正确，或者您可能未将其指定给链接器。

- 你可能已安装了32位版本的库，但你正在构建64位版，反之亦然。

- 库可能依赖于未安装的其他库。

若要修复某个路径问题，请验证是否已设置 LIB 环境变量，并为生成的每个配置包含你使用的库的所有目录。 在 IDE 中，LIB 变量通过 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)上的 "**库目录**" 属性进行设置。 对于生成的每个配置，请确保此处列出了包含所需库的所有目录。

如果需要提供替代标准库目录的库目录，可以在命令行中使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项，也可以在 IDE 中使用 "配置属性" 中的 "**附加库目录**" 属性。 **> 链接器 >** 项目的 "常规属性" 页。

请确保已安装所生成配置所需的每个版本的库。 请考虑使用[vcpkg](../../vcpkg.md)包管理实用程序来自动执行许多常见库的安装和设置。 当你可以时，最好是构建你自己的第三方库的副本，因此，你可以确定库所需的所有本地依赖项，并且它们的配置与项目相同。

### <a name="cannot-open-a-file-built-by-your-project"></a>无法打开项目生成的文件

如果*文件名由*解决方案生成，但在链接器尝试访问它时尚不存在，则可能会看到此错误。 如果一个项目依赖于另一个项目，但这些项目未按正确的顺序生成，就会发生这种情况。 若要解决此问题，请确保在使用该文件的项目中设置项目引用，以便在需要时生成缺失的文件。 有关详细信息，请参阅[在 Visual Studio C++项目中添加引用](../../build/adding-references-in-visual-cpp-projects.md)和[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。

### <a name="cannot-open-file-cprogramobj"></a>无法打开文件 "C：\\Program .obj"

如果你看到此错误，或者在驱动器的根目录中涉及到意外的 .obj 文件的类似错误，则问题几乎当然就是不是用双引号括起来的库路径。

若要修复命令行生成的此问题，请检查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项参数、LIB 环境变量中指定的路径和命令行中指定的路径，并确保在包含空格的任何路径两侧使用双引号。

若要在 IDE 中修复此问题，请在 "配置属性" [> "VC + + 目录](../../build/reference/vcpp-directories-property-page.md) **" 属性**页上，选中 "配置属性" 中的 "**附加库目录**" 属性 **> 链接器> 常规**"属性页和" 配置 "属性中的"**附加依赖项**"属性 **> 链接器 >** 项目的" 输入 "属性页。 如有必要，请确保所有包含所需库的目录路径都用双引号括起来。

### <a name="other-common-issues"></a>其他常见问题

当在命令行上或[#pragma 注释（lib，"library_name"）](../../preprocessor/comment-c-cpp.md)指令中指定给链接器的库文件名或路径不正确，或者路径具有无效的驱动器规格时，会发生此错误。 检查拼写和文件扩展名，并验证文件是否存在于指定位置。

另一个程序可能已打开该文件，链接器无法向其写入。 防病毒程序通常会暂时阻止访问新创建的文件。 若要解决此问题，请尝试从防病毒扫描程序中排除你的项目生成目录。

如果你使用的是并行生成选项，则 Visual Studio 可能已在另一个线程上锁定文件。 若要解决此问题，请验证是否在多个项目中生成了相同的代码对象或库，并使用生成依赖项或项目引用选取项目中的生成的二进制文件。

如果直接在 "**其他依赖项**" 属性中指定单独的库，请使用空格分隔库名称，而不是逗号或分号。 如果使用 "**编辑**" 菜单项打开 "**其他依赖项**" 对话框，请使用换行符分隔名称（而不是逗号、分号或空格）。 在 "**库目录**" 和 "**其他库目录**" 对话框中指定库路径时，还可以使用换行符。

当*filename*的路径扩展到超过260个字符时，可能会看到此错误。 如果需要，请更改名称或重新排列目录结构，以缩短所需文件的路径。

发生此错误的原因可能是文件过大。 如果库或对象文件的大小超过千兆字节，则可能会导致32位链接器出现问题。 此问题的可能解决方法是使用64位工具集。 有关如何在命令行执行此操作的详细信息，请参阅[如何：在命令行](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)上启用 64 C++位可视化工具集。 有关如何在 IDE 中执行此操作的信息，请参阅[将 MSBuild 用于64位编译器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和本 Stack Overflow post：[如何使 Visual Studio 使用本机 amd64 工具链](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

如果您的文件权限不足，无法访问*文件名*，则会出现此错误。 如果你使用普通用户帐户并尝试访问受保护的系统目录中的库文件，或使用从具有原始权限集的其他用户复制的文件，则可能会发生这种情况。 若要解决此问题，请将文件移动到可写入的项目目录。 如果文件在可写目录中，但权限不可访问，则可以使用管理员命令提示符并运行 takeown 命令，以获取文件的所有权。

如果没有足够的磁盘空间，则会发生此错误。 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，也可以使用非常大的链接来耗尽或分段可用磁盘空间。 请考虑使用[/opt （优化）](../../build/reference/opt-optimizations.md)选项;执行可传递的 COMDAT 消除多次读取所有对象文件。

如果*文件名*为 .lnk*nnn*（这是由临时文件的链接器生成的文件名），则 tmp 环境变量中指定的目录可能不存在，或者可以为 TMP 环境变量指定多个目录。 只应为 TMP 环境变量指定一个目录路径。
