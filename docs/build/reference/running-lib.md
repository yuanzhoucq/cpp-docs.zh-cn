---
title: 运行 LIB
ms.date: 09/28/2018
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 73a259faa57d74fbe535bfa329dfc2a39cb6bbad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656971"
---
# <a name="running-lib"></a>运行 LIB

可以控制 LIB 使用各种命令行选项。

## <a name="lib-command-line"></a>LIB 命令行

若要运行 LIB，键入命令`lib`跟选项和任务的文件名称使用 LIB 来执行。 LIB 还接受命令行输入命令文件，以下部分所述。 LIB 不使用环境变量。

> [!NOTE]
> 如果您习惯于 LINK32.exe 和 LIB32.exe 工具提供与 Microsoft Win32 软件开发工具包的 Windows NT 中，您可能一直使用这两个命令`link32 -lib`或命令`lib32`来管理库和创建导入的库。 请务必更改你的生成文件和批处理文件使用`lib`命令。

## <a name="lib-command-files"></a>LIB 命令文件

可以将命令行参数传递到 LIB 在命令文件中使用以下语法：

> **LIB \@**  <em>commandfile</em>

该文件*commandfile*是一个文本文件。 无空格或制表符之间允许 at 符号 (**\@**) 和文件名称。 没有默认扩展名;必须指定完整的文件名，包括任何扩展。 不能使用通配符。 可以使用的文件的名称来指定绝对或相对路径。

在命令文件中，参数可以分隔空格或制表符，因为它们可以在命令行;它们还可以由换行符分隔。 使用分号 (**;**) 来标记注释。 LIB 忽略从分号到行尾的所有文本。

您可以在命令文件中，指定所有或命令行的一部分，并且可以使用多个 LIB 命令中的命令文件。 LIB 接受命令文件输入，如同它命令行上该位置中指定。 不能嵌套命令文件。 LIB 回显命令文件的内容，除非使用 /NOLOGO 选项。

## <a name="using-lib-options"></a>使用 LIB 选项

选项包括为任一短划线选项说明符 (**-**) 或正斜杠 (**/**) 后, 跟的选项的名称。 不能缩写选项名称。 某些选项带自变量，指定在冒号 (**:**)。 中的选项规范允许空格或制表符。 使用一个或多个空格或制表符分隔命令行上的选项规范。 选项名及其关键字或文件的参数不区分大小写，但使用作为参数的标识符区分大小写。 LIB 处理选项和命令文件中的命令行上指定的顺序。 如果使用不同的参数重复一个选项，要处理的最后一个优先。

以下选项适用于所有 LIB 的模式：

> **/ERRORREPORT** [**NONE** &AMP;#124; **提示** &AMP;#124; **队列** &AMP;#124; **发送**]

如果 lib.exe 在运行时失败，则可以使用 **/ERRORREPORT**有关这些内部错误向 Microsoft 发送信息。

有关详细信息 **/ERRORREPORT**，请参阅[/errorReport （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。

> **/LTCG**

"LTCG"代表*链接时间代码生成*。 此功能要求编译器之间的合作 ([cl.exe](compiler-options.md))，LIB 和链接器 ([链接](linker-options.md)) 以优化受任何组件可以单独执行的操作的代码。

为 LIB **/LTCG**选项指定 cl.exe 的输入，包括使用生成的对象文件[/GL](gl-whole-program-optimization.md)编译器选项。 如果 LIB 遇到这种输入并 **/LTCG**未指定，则它将使用显示信息性消息后，将启用 /LTCG 重新启动。 换而言之，不需要显式设置此选项，但它可以提高生成性能，若要这样做，因为不需要重启 LIB。

在生成过程中，LIB 的输出发送到链接。 链接都有其自己单独 **/LTCG**它用于执行各种优化，包括全程序优化和配置文件按配置优化 (PGO) 检测的选项。 有关链接选项的详细信息，请参阅[/LTCG](ltcg-link-time-code-generation.md)。

> **/MACHINE**

指定程序的目标平台。 通常情况下，不需要指定 /MACHINE。 LIB 推断出的.obj 文件中的计算机类型。 但是，在某些情况下，LIB 无法确定计算机类型，并发出一条错误消息。 如果发生此类错误，则指定 /MACHINE。 在 /EXTRACT 模式下，此选项适用于仅限验证。 使用`lib /?`在命令行以查看可用的计算机类型。

> **/NOLOGO**

取消显示 LIB 版权消息和版本，并防止回显命令文件。

> **/VERBOSE**

显示有关进度的会话，包括要添加的.obj 文件的名称的详细信息。 信息被发送到标准输出，并可重定向到文件。

> **/WX**[**： 否**]

将警告视为错误。 请参阅[/WX （将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)有关详细信息。

其他选项仅适用于特定的 LIB 模式。 这些选项描述每种模式的各节所述。

## <a name="see-also"></a>请参阅

[LIB 引用](../../build/reference/lib-reference.md)
