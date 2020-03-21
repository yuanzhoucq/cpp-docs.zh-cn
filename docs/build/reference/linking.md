---
title: MSVC 链接器参考
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079515"
---
# <a name="linking"></a>链接

在C++项目中，在编译器将源代码编译到对象文件（* .obj）之后，将执行*链接*步骤。 链接器（link）将对象文件合并为一个可执行文件。

可在 Visual Studio 内部或外部设置链接器选项。 在 Visual Studio 中，通过在**解决方案资源管理器**中右键单击项目节点，然后选择 "**属性**" 以显示属性页，即可访问链接器选项。 选择左窗格中的 "**链接器**"，展开节点并查看所有选项。

## <a name="linker-command-line-syntax"></a>链接器命令行语法

在 Visual Studio 外部运行链接时，可以通过一种或多种方式指定输入：

- 在命令行上

- 使用命令文件

- 在环境变量中

LINK first 处理在 LINK 环境变量中指定的选项，后跟在命令行和命令文件中指定这些选项的顺序。 如果使用不同的参数重复选项，则将优先处理最后一个选项。

选项应用于整个生成;不能将任何选项应用于特定的输入文件。

运行链接。EXE，请使用以下命令语法：

```
LINK arguments
```

`arguments` 包括选项和文件名，可以按任意顺序指定。 首先处理选项，然后处理文件。 使用一个或多个空格或制表符分隔参数。

> [!NOTE]
>  只能从 Visual Studio 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

## <a name="command-line"></a>命令行

在命令行中，选项由选项说明符（破折号（-）或正斜杠（/））组成，后跟选项的名称。 不能缩写选项名称。 某些选项采用一个自变量，在冒号（:) 之后指定。 选项规范内不允许有空格或制表符，除非在/COMMENT 选项中带引号的字符串中。 以十进制或 C 语言表示法指定数值参数。 选项名及其关键字或文件名参数不区分大小写，但作为参数的标识符区分大小写。

若要将文件传递给链接器，请在命令行上的 LINK 命令后指定文件名。 您可以使用文件名指定绝对路径或相对路径，也可以在文件名中使用通配符。 如果省略点（.）和文件扩展名，则 LINK 假定 .obj 用于查找文件。 LINK 不使用文件扩展名或缺少它们来对文件内容进行假设;它通过检查来确定文件的类型，并相应地对其进行处理。

如果成功，则 link 返回零（无错误）。  否则，链接器将返回停止链接的错误号。  例如，如果链接器生成 LNK1104，则链接器将返回1104。  相应地，链接器错误返回的错误号越小，就是1000。  返回值128表示操作系统或 .config 文件存在配置问题;加载程序未加载 share.exe 或 c2。

## <a name="link-command-files"></a>LINK 命令文件

可以将命令行参数传递到命令文件格式的链接。 若要为链接器指定命令文件，请使用以下语法：

> **链接 \@** <em>commandfile</em>

*Commandfile*是文本文件的名称。 At 符号（ **\@** ）和文件名之间不允许有空格或制表符。 没有默认扩展;您必须指定完整的文件名，包括任何扩展名。 不能使用通配符。 您可以使用文件名指定绝对路径或相对路径。 LINK 不使用环境变量搜索该文件。

在命令文件中，参数可以由空格或制表符分隔（在命令行上）和换行符。

可以在命令文件中指定全部或部分命令行。 可以在 LINK 命令中使用多个命令文件。 LINK 接受命令文件输入，就如同在命令行的该位置中指定的一样。 命令文件不能嵌套。 除非指定了[/nologo](nologo-suppress-startup-banner-linker.md)选项，否则 LINK 回显命令文件的内容。

## <a name="example"></a>示例

以下用于生成 DLL 的命令将对象文件和库的名称传递到单独的命令文件中，并使用第三个命令文件来规范/EXPORTS 选项：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK 环境变量

LINK 工具使用以下环境变量：

- LINK 并 \_链接\_（如果已定义）。 LINK 工具添加了 LINK 环境变量中定义的选项和参数，并在处理前将 \_链接\_ 环境变量中定义的选项和参数追加到命令行参数。

- LIB（如已定义）。 当在命令行上或使用[/base](base-base-address.md)选项搜索指定的对象、库或其他文件时，链接工具会使用 LIB 路径。 它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。 LIB 变量可以包含一个或多个路径规范，用分号分隔。 一个路径必须指向 Visual C++ 安装的 \lib 子目录。

- PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。 （LINK 要求 CVTRES 链接 .res 文件。）路径必须指向视觉对象C++安装的 \bin 子目录。

- TMP，用于链接 OMF 或.res 文件时指定目录。

## <a name="see-also"></a>另请参阅

[C/C++构建引用](c-cpp-building-reference.md)
[MSVC 链接器选项](linker-options.md)
[模块定义（.Def）文件](module-definition-dot-def-files.md)
[链接器支持延迟加载的 dll](linker-support-for-delay-loaded-dlls.md)
