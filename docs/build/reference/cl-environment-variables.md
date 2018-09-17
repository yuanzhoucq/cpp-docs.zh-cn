---
title: CL 环境变量 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74ac2cb1ad28720cc45aec4f6258d1152a55e861
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722730"
---
# <a name="cl-environment-variables"></a>CL 环境变量

CL 工具使用以下环境变量:

- CL 和\_CL\_，如果定义。 CL 工具前面添加的选项和参数到命令行自变量，在 CL 环境变量中定义并追加选项和参数中定义\_CL\_之前处理。

- INCLUDE，必须指向 Visual C++ 安装的 \include 子目录。

- LIBPATH，指定要搜索引用的元数据文件的目录[#using](../../preprocessor/hash-using-directive-cpp.md)。 有关 LIBPATH 的详细信息，请参阅 `#using`。

您可以设置 CL 或\_CL\_环境变量使用以下语法：

> 设置 CL = [[*选项*]...[*文件*]...][/link*链接选择*...]设置\_CL\_= [[*选项*]...[*文件*]...][/link*链接选择*...]

有关 CL 的参数的详细信息和\_CL\_环境变量，请参阅[编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)。

可以使用这些环境变量定义最常使用的文件和选项，并使用命令行为特定用途定义特定文件和选项。 CL 和\_CL\_环境变量被限制为 1024年个字符 （命令行输入限制）。

不能使用 /D 选项定义使用等号 (=) 的符号。 可以将等号替换为数字符号 (#)。 在这种方式，可以使用 CL 或\_CL\_环境变量来定义具有显式值的预处理器常量 — 例如，`/DDEBUG#1`可以定义`DEBUG=1`。

有关相关信息，请参阅[设置环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>示例

下面是设置 CL 环境变量的示例：

> 设置 CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

设置此环境变量时，如果输入`CL INPUT.C`在命令行中，这是有效的命令：

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ 输入。C

下面的示例使普通 CL 命令编译源文件 FILE1.c 和 FILE2.c，然后链接对象文件 FILE1.obj、FILE2.obj 和 FILE3.obj：

> 设置 CL = FILE1。C FILE2。C 集\_CL\_= FILE3。OBJ CL

这与下面的命令行的效果相同：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>请参阅

[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)
