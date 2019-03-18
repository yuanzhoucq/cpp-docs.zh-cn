---
title: MSVC 链接器引用
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820372"
---
# <a name="linking"></a>链接

在 c + + 项目中，*链接*编译器已将源代码编译到对象文件 (*.obj) 后，执行步骤。 链接器 (link.exe) 将对象文件合并到单个可执行文件。 

内部或外部 Visual Studio，可以设置链接器选项。 通过右键单击项目节点，在 Visual Studio 中，访问链接器选项**解决方案资源管理器**，然后选择**属性**显示属性页。 选择**链接器**在左窗格中展开节点，并查看所有选项。 


## <a name="linker-command-line-syntax"></a>链接器命令行语法

当您运行 Visual Studio 外部链接时，可以在一个或多个方面来指定输入：

- 在命令行上

- 使用命令文件

- 在环境变量中

链接第一个处理指定的选项在链接的环境变量中，然后按照它们在命令行指定的顺序和命令文件中的选项。 如果一个选项重复使用不同的参数，处理的最后一个优先。

选项适用于整个生成;无选项可以应用于特定的输入文件。

若要运行链接。Exe 文件，请使用以下命令语法：

```
LINK arguments
```

`arguments`包括选项和文件名，可以按任意顺序指定。 选项为已处理的第一个，则文件。 使用一个或多个空格或制表符分隔的参数。

> [!NOTE]
>  可以仅从 Visual Studio 命令提示符启动此工具。 无法从系统命令提示符或文件资源管理器中启动它。

## <a name="command-line"></a>命令行

在命令行选项选项说明符组成，短划线 （-） 或正斜杠 （/） 后, 跟的选项的名称。 不能缩写选项名称。 某些选项带自变量，在冒号 （:） 后指定。 不包含空格或选项卡允许选项规范中除 /COMMENT 选项中带引号的字符串中。 以十进制或 C 语言表示法指定数值参数。 选项名及其关键字或 filename 参数不区分大小写，但用作参数的标识符区分大小写。

要传递给链接器文件，请链接命令后在命令行上指定文件名。 可以指定绝对或相对路径与文件名，并可以在文件名中使用通配符。 如果省略句点 （.） 和文件扩展名，链接将假定.obj 用于查找文件。 链接不使用文件扩展名或缺乏进行假设内容的文件;它会通过检查，确定文件的类型并相应地对其进行处理。

link.exe 将返回零表示成功 （无错误）。  否则，链接器返回停止该链接的错误号。  例如，如果链接器生成了 LNK1104，链接器将返回 1104年。  相应地，链接器返回的错误上最小错误编号为 1000年。  返回值 128 表示操作系统或.config 文件; 的配置问题加载程序未加载 link.exe 或 c2.dll。

## <a name="link-command-files"></a>LINK 命令文件

可以将命令行参数传递到命令文件的窗体中的链接。 若要指定链接器的命令文件，请使用以下语法：

> **链接\@**  <em>commandfile</em>

*Commandfile*是文本文件的名称。 无空格或制表符之间允许 at 符号 (**\@**) 和文件名。 没有默认扩展名;必须指定完整的文件名，包括任何扩展。 不能使用通配符。 使用文件名，可以指定绝对或相对路径。 链接不使用环境变量来搜索该文件。

在命令文件中，参数可以分隔空格或制表符 （在命令行中） 和由换行符。

可以在命令文件中指定的命令行全部或部分。 可以使用多个链接命令中的命令文件。 链接接受命令文件输入，如同它命令行上该位置中指定。 不能嵌套命令文件。 链接将回显命令文件的内容，除非[/NOLOGO](nologo-suppress-startup-banner-linker.md)指定选项。

## <a name="example"></a>示例

以下命令以生成 DLL 在单独的命令文件中传递的对象文件和库的名称，并将第三个命令 /EXPORTS 选项的文件：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK 环境变量

LINK 工具使用以下环境变量：

- 链接和\_链接\_，如果定义。 LINK 工具预置的选项和链接的环境变量中定义的自变量并追加选项和参数中定义\_链接\_之前处理的命令行自变量的环境变量。

- LIB（如已定义）。 LINK 工具搜索对象、 库或在命令行上或通过指定其他文件时使用 LIB 路径[/base](base-base-address.md)选项。 它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。 LIB 变量可以包含一个或多个路径规范，用分号分隔。 一个路径必须指向 Visual C++ 安装的 \lib 子目录。

- PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。 （LINK 需要 CVTRES 链接 .res 文件。）PATH 必须指向 Visual C++ 安装的 \bin 子目录。

- TMP，用于链接 OMF 或.res 文件时指定目录。

## <a name="see-also"></a>请参阅

[C/c + + 生成参考](c-cpp-building-reference.md)
[MSVC 链接器选项](linker-options.md)
[模块定义 (.def) 文件](module-definition-dot-def-files.md)
[的链接器支持延迟加载 Dll](linker-support-for-delay-loaded-dlls.md)
