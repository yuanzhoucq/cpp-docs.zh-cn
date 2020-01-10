---
title: 链接器工具错误 LNK1104
description: 描述 Microsoft C 和C++ （MSVC）链接器错误 LNK1104、其原因和可能的解决方案。
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 8878db1b0829703b22b2f7863eb7955d17ad3096
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301777"
---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104

> 无法打开文件 "*filename*"

如果链接器未能打开文件（用于读取或写入），则会报告此错误。 此问题的两个最常见原因是：

- 您的程序已在运行或加载到调试器中，并且

- 库路径不正确，或者没有用双引号括起来。

此错误还有很多其他可能的原因。 若要缩小其范围，请先*检查文件名的类型是什么*。 然后，使用下列部分来帮助确定并解决特定问题。

## <a name="cant-open-your-app-or-its-pdb-file"></a>无法打开应用或其 .pdb 文件

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>应用正在运行，或已加载到调试器中

当*filename*是可执行文件的名称或关联的 .pdb 文件时，请查看应用程序是否已在运行。 然后检查它是否已加载到调试器中。 若要解决此问题，请先停止程序并从调试器中卸载它，然后再重新生成它。 如果应用已在其他程序（如资源编辑器）中打开，请将其关闭。 如果程序没有响应，则可能需要使用任务管理器来结束进程。 你可能还需要关闭并重新启动 Visual Studio。

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>你的应用已被防病毒扫描锁定

防病毒程序通常会暂时阻止对新创建的文件（尤其是 .exe 和 .dll 可执行文件）的访问。 若要解决此问题，请尝试从防病毒扫描程序中排除你的项目生成目录。

## <a name="cant-open-a-microsoft-library-file"></a>无法打开 Microsoft 库文件

### <a name="windows-libraries-such-as-kernel32lib"></a>Windows 库，如 kernel32.dll

如果无法打开的文件是 Microsoft 提供的标准库文件之一（如*kernel32.dll*），则可能会出现项目配置错误或安装错误。 验证是否已安装 Windows SDK。 如果你的项目需要其他 Microsoft 库（如 MFC），请确保 Visual Studio 安装程序也安装了 MFC 组件。 你可以随时运行安装程序来添加可选组件。 有关详细信息，请参阅[修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 使用安装程序中的 "**单个组件**" 选项卡选择特定的库和 sdk。

### <a name="versioned-vcruntime-libraries"></a>版本控制 vcruntime 库

如果错误消息具有版本控制的 Microsoft 库（如*msvcr120.dll*），则可能无法安装该编译器版本的平台工具集。 若要解决此问题，可以使用两个选项：升级项目以使用当前平台工具集，或者安装旧版工具集并不更改项目。 有关详细信息，请参阅[从C++ visual Studio 的早期版本升级项目](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用 visual Studio 中的本机多目标来生成旧项目](../../porting/use-native-multi-targeting.md)。

### <a name="retail-debug-or-platform-specific-libraries"></a>零售、调试或特定于平台的库

首次生成新的目标平台或配置（例如零售或 ARM64）时，可能会发生此错误。 在 IDE 中，验证是否安装了 "[常规" 属性页](../../build/reference/general-property-page-project.md)中指定的**平台工具集**和**Windows SDK 版本**。 另外，请验证在 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)中指定的**库目录**中是否提供了所需的库。 检查每个配置的属性，例如 "调试"、"零售"、"x86" 或 "ARM64"。 如果一个生成工作而另一个生成不工作，则比较这两个版本的设置。 安装任何缺少的必需工具和库。

### <a name="the-vccorliblib-library"></a>Vccorlib.h 库

对于通用 Windows （UWP）应用或组件，没有 Spectre 的库。 如果错误消息中包含*vccorlib.h*，则可能已在 UWP 项目中启用了[/Qspectre](../../build/reference/qspectre.md) 。 禁用 **/Qspectre**编译器选项以解决此问题。 在 Visual Studio 中，更改**Spectre 缓解**属性。 它可在 "项目**属性页**" 对话框的 " **CC++ /**  > **代码生成**" 页中找到。

### <a name="libraries-in-projects-from-online-or-other-sources"></a>在线或其他源中的项目中的库

如果生成的项目是从另一台计算机复制的，则库安装位置可能会不同。 对于命令行生成，请验证是否为生成正确设置了 LIB 环境变量和库路径。 在 Visual Studio 中，可以查看和编辑在项目的属性页中设置的当前库路径。 在 " **VC + + 目录**" 页上，选择 "**库目录**" 属性的下拉控件，然后选择 "**编辑**"。 "**库目录**" 对话框的 "**计算值**" 部分列出了为库文件搜索的当前路径。 更新这些路径以指向你的本地库。

### <a name="updated-windows-sdk-libraries"></a>更新 Windows SDK 库

如果 Windows SDK 的 Visual Studio 路径过期，则会出现此错误。 如果你独立于 Visual Studio 安装程序安装较新的 Windows SDK，则可能会发生这种情况。 若要在 IDE 中修复此问题，请更新在 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)中指定的路径。 设置路径中的版本以匹配新的 SDK。 如果使用开发人员命令提示，请使用新的 SDK 路径更新用于初始化环境变量的批处理文件。 可以通过使用 Visual Studio 安装程序安装更新的 Sdk 来避免此问题。

## <a name="cant-open-a-third-party-library-file"></a>无法打开第三方库文件

此问题有几个常见的原因：

- 库文件的路径可能不正确，也可能不会括在双引号中。 或者，您可能未将其指定给链接器。

- 你可能已经安装了32位版本的库，但生成的是64位或其他方法。

- 库可能依赖于未安装的其他库。

若要修复命令行生成的路径问题，请验证是否已设置 LIB 环境变量。 请确保它包括所有使用的库的路径，以及生成的每个配置的路径。 在 IDE 中，由**VC + + 目录**设置的库路径 > **库目录**"属性。 对于生成的每个配置，请确保此处列出了包含所需库的所有目录。

你可能需要提供替代标准库目录的库目录。 在命令行中，使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项。 在 IDE 中，使用 "配置属性" 中的 "**附加库目录**" 属性 **> 链接器 >** 项目的 "常规属性" 页。

请确保安装所生成的配置所需的每个版本的库。 请考虑使用[vcpkg](../../vcpkg.md)包管理实用程序来自动执行许多常见库的安装和设置。 当你可以时，最好构建你自己的第三方库副本。 然后，确保为与项目相同的配置生成了所有库的本地依赖项。

## <a name="cant-open-a-file-built-by-your-project"></a>无法打开项目生成的文件

如果*filename*在链接器尝试访问时尚不存在，则可能会看到此错误。 如果一个项目依赖于解决方案中的另一个项目，但项目以错误的顺序进行生成，则会发生这种情况。 若要解决此问题，请确保在使用该文件的项目中设置项目引用。 然后，缺少的文件在需要之前生成。 有关详细信息，请参阅[在 Visual Studio C++项目中添加引用](../../build/adding-references-in-visual-cpp-projects.md)和[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。

## <a name="cannot-open-file-cprogramobj"></a>无法打开文件 "C：\\Program .obj"

如果在错误消息中看到文件名*C：\\Program* ，请将库路径包装为双引号。 当以*C：\\程序文件*开头的未解包路径传递给链接器时，将发生此错误。 已解包的路径也可能导致类似的错误。 通常，它们在驱动器的根目录中显示意外的 .obj 文件。

若要修复命令行生成的此问题，请检查[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项参数。 同时检查 LIB 环境变量中指定的路径，以及在命令行上指定的路径。 请确保在包含空格的任何路径前后使用双引号。

若要在 IDE 中解决此问题，请在项目的下列属性中添加双引号：

- [配置属性 > "VC + + 目录](../../build/reference/vcpp-directories-property-page.md)" 属性页上的 "**库目录**" 属性

- 配置属性中的 "**附加库目录**" 属性 **> 链接器 > 常规**属性页，

- 配置属性中的 "**其他依赖项**" 属性 **> 链接器 > "输入**" 属性页。

## <a name="other-common-issues"></a>其他常见问题

### <a name="path-or-filename-issues"></a>路径或文件名问题

如果为链接器指定的库文件名或路径不正确，则会发生此错误。 如果路径具有无效的驱动器规格，则为或。 查看命令行或任何[#pragma 注释（lib、"library_name"）](../../preprocessor/comment-c-cpp.md)指令中是否存在问题。 检查拼写和文件扩展名，并验证文件是否存在于指定位置。

### <a name="parallel-build-synchronization"></a>并行生成同步

如果使用的是并行生成选项，则 Visual Studio 可能已在另一个线程上锁定文件。 若要解决此问题，请验证是否在多个项目中生成了相同的代码对象或库。 使用生成依赖项或项目引用选取项目中的生成的二进制文件。

### <a name="additional-dependencies-specified-in-the-ide"></a>IDE 中指定的其他依赖项

如果直接在 "**其他依赖项**" 属性中指定单独的库，请使用空格分隔库名称。 不要使用逗号或分号。 如果使用 "**编辑**" 菜单项打开 "**其他依赖项**" 对话框，请使用换行符分隔名称（而不是逗号、分号或空格）。 在 "**库目录**" 和 "**其他库目录**" 对话框中指定库路径时，还可以使用换行符。

### <a name="paths-that-are-too-long"></a>过长的路径

当*filename*的路径扩展到超过260个字符时，可能会看到此错误。 如果需要，请重新排列你的目录结构或缩短你的文件夹和文件名以缩短路径。

### <a name="files-that-are-too-large"></a>文件太大

发生此错误的原因可能是文件过大。 如果库或对象文件的大小超过千兆字节，则可能会导致32位链接器出现问题。 此问题的可能解决方法是使用64位工具集。 有关如何在命令行中使用64位工具集的详细信息，请参阅[如何：在命令行上启用64位可视化C++工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 有关如何在 IDE 中使用64位工具集的信息，请参阅[将 MSBuild 与64位编译器和工具配合使用](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)。 另请参阅此 Stack Overflow post：[如何使 Visual Studio 使用本机 amd64 工具链](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

### <a name="incorrect-file-permissions"></a>文件权限不正确

如果您的文件权限不足，无法访问*文件名*，则会出现此错误。 如果你使用普通用户帐户来访问受保护的系统目录中的库文件，则可能会发生这种情况。 或者，如果你使用的是从其他用户复制的文件，而这些文件仍具有原始权限集。 若要解决此问题，请将文件移动到可写入的项目目录。 如果移动的文件具有不可访问的权限，请在管理员命令窗口中运行 takeown 命令，以获取文件的所有权。

### <a name="insufficient-disk-space"></a>磁盘空间不足

如果没有足够的磁盘空间，则会发生此错误。 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，大链接也可以耗尽或分段可用磁盘空间。 请考虑使用[/opt （优化）](../../build/reference/opt-optimizations.md)选项;执行可传递的 COMDAT 消除多次读取所有对象文件。

### <a name="problems-in-the-tmp-environment-variable"></a>TMP 环境变量中的问题

如果*文件名*为 .lnk*nnn*，则它是一个用于临时文件的链接器生成的文件名。 TMP 环境变量中指定的目录可能不存在。 或者，可以为 TMP 环境变量指定多个目录。 只应为 TMP 环境变量指定一个目录路径。

## <a name="help-my-issue-isnt-listed-here"></a>我的问题未在此处列出！

如果此处未列出任何问题，则可以使用 Visual Studio 中的反馈工具获取帮助。 在 IDE 中，请在菜单栏上，选择 "**帮助 > 发送反馈 > 报告问题**。 或者，通过使用帮助 **> 发送反馈 > 发送建议**来提交建议。 你还可以使用 Visual Studio C++ [开发人员社区](https://developercommunity.visualstudio.com/spaces/62/index.html)网站。 使用它搜索问题的答案并寻求帮助。 有关详细信息，请参阅[如何报告 Visual C++工具集或文档的问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果你发现了解决此问题的一种新方法，我们应该将其添加到本文中，请告知我们。 你可以**使用以下按钮**向我们发送反馈。 使用它在[ C++文档 GitHub](https://github.com/MicrosoftDocs/cpp-docs/issues)存储库中创建新问题。 谢谢!
