---
title: MSVC 链接器参考
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336490"
---
# <a name="linking"></a>链接

在C++项目中，*链接*步骤在编译器将源代码编译为对象文件 （*.obj） 后执行。 链接器 （link.exe） 将对象文件合并到单个可执行文件中。

链接器选项可以设置在视觉工作室内外。 在 Visual Studio 中，您可以右键单击**解决方案资源管理器**中的项目节点并选择 **"属性**"来显示属性页，从而访问链接器选项。 在左侧窗格中选择 **"链接器**"以展开节点并查看所有选项。

## <a name="linker-command-line-syntax"></a>链接器命令行语法

在 Visual Studio 外部运行 LINK 时，可以通过一种或多种方式指定输入：

- 在命令行上

- 使用命令文件

- 在环境变量中

LINK 首先处理在 LINK 环境变量中指定的选项，然后按照在命令行和命令文件中指定的选项的顺序处理这些选项。 如果使用不同的参数重复一个选项，则最后处理的选项优先。

选项应用于整个生成;不能将任何选项应用于特定的输入文件。

运行 LINK。EXE，使用以下命令语法：

```
LINK arguments
```

包括`arguments`选项和文件名，可以按任意顺序指定。 首先处理选项，然后处理文件。 使用一个或多个空格或选项卡分隔参数。

> [!NOTE]
> 只能从可视化工作室命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

## <a name="command-line"></a>命令行

在命令行上，选项由选项指定器组成，即破折号 （-） 或向前斜杠 （/），后跟选项的名称。 不能缩写选项名称。 某些选项采用在冒号（:)）之后指定的参数。 选项规范中不允许空格或选项卡，但 /COMMENT 选项中的引用字符串中除外。 以小数或 C 语言表示法指定数值参数。 选项名称及其关键字或文件名参数不区分大小写，但标识符作为参数区分大小写。

要将文件传递给链接器，请在 LINK 命令之后在命令行上指定文件名。 您可以使用文件名指定绝对路径或相对路径，也可以在文件名中使用通配符。 如果省略点 （.） 和文件名扩展名，LINK 将假定 .obj 用于查找文件。 LINK 不使用文件名扩展名或缺少文件扩展名来对文件内容进行假设;它通过检查确定文件的类型，并相应地处理它。

link.exe 返回零以求成功（无错误）。  否则，链接器将返回停止链接的错误编号。  例如，如果链接器生成 LNK1104，则链接器返回 1104。  因此，链接器在错误时返回的最低错误数为 1000。  返回值 128 表示操作系统或 .config 文件的配置问题;加载程序未加载链接.exe 或 c2.dll。

## <a name="link-command-files"></a>LINK 命令文件

可以将命令行参数以命令文件的形式传递给 LINK。 要向链接器指定命令文件，请使用以下语法：

> **链接\@**<em>命令文件</em>

*命令文件*是文本文件的名称。 在 at 符号 （**\@**） 和文件名之间不允许空格或选项卡。 没有默认扩展;因此，没有默认扩展。必须指定完整的文件名，包括任何扩展名。 无法使用通配符。 您可以使用文件名指定绝对路径或相对路径。 LINK 不使用环境变量来搜索文件。

在命令文件中，参数可以由空格或选项卡（如命令行）和换行符分隔。

您可以在命令文件中指定命令行的全部或部分。 您可以在 LINK 命令中使用多个命令文件。 LINK 接受命令文件输入，就好像它是在命令行上的该位置指定的一样。 无法嵌套命令文件。 LINK 与命令文件的内容相呼应，除非指定[了 /NOLOGO](nologo-suppress-startup-banner-linker.md)选项。

## <a name="example"></a>示例

生成 DLL 的以下命令将对象文件和库的名称传递到单独的命令文件中，并使用第三个命令文件来规范 /EXPORTS 选项：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK 环境变量

LINK 工具使用以下环境变量：

- 链接和\_链接\_，如果已定义。 LINK 工具预先准备了 LINK 环境变量中定义的选项和参数，并在处理之前将\_LINK\_环境变量中定义的选项和参数追加到命令行参数。

- LIB（如已定义）。 LINK 工具在搜索命令行或[/BASE](base-base-address.md)选项上指定的对象、库或其他文件时使用 LIB 路径。 它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。 LIB 变量可以包含一个或多个路径规范，用分号分隔。 一个路径必须指向 Visual C++ 安装的 \lib 子目录。

- PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。 （LINK 要求 CVTRES 链接 .res 文件。PATH 必须指向可视化C++安装的 \bin 子目录。

- TMP，用于链接 OMF 或.res 文件时指定目录。

## <a name="see-also"></a>另请参阅

[C/C++ 构建参考](c-cpp-building-reference.md)
[MSVC 链接器选项](linker-options.md)
[模块定义 （.def） 文件](module-definition-dot-def-files.md)
[链接器支持延迟加载的 DLL](linker-support-for-delay-loaded-dlls.md)
