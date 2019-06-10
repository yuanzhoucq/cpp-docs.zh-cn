---
title: CL 环境变量
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821530"
---
# <a name="cl-environment-variables"></a>CL 环境变量

CL 工具使用以下环境变量:

- CL 和\_CL_，如果定义。 CL 工具前面添加的选项和参数到命令行自变量，在 CL 环境变量中定义并追加选项和参数中定义\_CL_ 之前处理。

- 包括必须指向 Visual Studio 安装的 \include 子目录。

- LIBPATH，指定要搜索引用的元数据文件的目录[#using](../../preprocessor/hash-using-directive-cpp.md)。 有关 LIBPATH 的详细信息，请参阅[#using](../../preprocessor/hash-using-directive-cpp.md)。

您可以设置 CL 或\_CL_ 环境变量使用以下语法：

> 设置 CL = [[*选项*]...[*文件*]...][/link*链接选择*...] \
> 设置\_CL\_= [[*选项*]...[*文件*]...][/link*链接选择*...]

有关 CL 的参数的详细信息和\_CL_ 环境变量，请参阅[MSVC 编译器命令行语法](compiler-command-line-syntax.md)。

可以使用这些环境变量来定义的文件和最常使用的选项。 然后使用命令行来为特定目的而改为 CL 提供更多的文件和选项。 CL 和\_CL_ 环境变量被限制为 1024年个字符 （命令行输入限制）。

不能使用[/D](d-preprocessor-definitions.md)选项来定义符号的使用等号 ( **=** )。 相反，可以使用数字符号 ( **#** ) 等号。 在这种方式，可以使用 CL 或\_CL_ 环境变量来定义具有显式值的预处理器常量 — 例如，`/DDEBUG#1`定义`DEBUG=1`。

有关相关信息，请参阅[设置环境变量](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>示例

以下命令是设置 CL 环境变量的示例：

> 设置 CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

设置 CL 环境变量时，如果输入`CL INPUT.C`在命令行中，将成为有效的命令：

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

下面的示例使普通 CL 命令编译源文件 FILE1.c 和 FILE2.c，然后链接对象文件 FILE1.obj、FILE2.obj 和 FILE3.obj：

> 设置 CL = FILE1。C FILE2。C \
> SET \_CL_=FILE3.OBJ \
> CL

这些环境变量进行改为 CL 调用具有相同的效果，如以下命令行：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>请参阅

[设置编译器选项](compiler-command-line-syntax.md) \
[MSVC 编译器选项](compiler-options.md)
