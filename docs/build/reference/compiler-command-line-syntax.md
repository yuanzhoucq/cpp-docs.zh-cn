---
title: MSVC 编译器命令行语法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294338"
---
# <a name="compiler-command-line-syntax"></a>编译器命令行语法

CL 命令行使用以下语法：

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

下表介绍 CL 命令的输入。

|条目|含义|
|-----------|-------------|
|*option*|一个或多个[CL 选项](compiler-options.md)。 请注意，所有选项都应用于指定的源的所有文件。 由正斜杠 （/） 或短划线 （-） 指定选项。 如果某个选项带有参数，该选项的说明文档是否允许选项和参数之间有空格。 （除了 /HELP 选项） 的选项名称不区分大小写。 请参阅[CL 选项的顺序](order-of-cl-options.md)有关详细信息。|
|`file`|一个或多个源代码文件、.obj 文件或库的名称。 CL 编译源文件，并将链接器传递.obj 文件和库的名称。 请参阅[CL 文件名语法](cl-filename-syntax.md)有关详细信息。|
|*lib*|一个或多个库名称。 CL 将这些名称传递给链接器。|
|*command-file*|包含多个选项和文件名的文件。 请参阅[CL 命令文件](cl-command-files.md)有关详细信息。|
|*link-opt*|一个或多个[MSVC 链接器选项](linker-options.md)。 CL 将这些选项传递给链接器。|

只要在命令行上的字符数不超过 1024，由操作系统限制，可以指定任意数量的选项、 文件名和库名称。

Cl.exe 的返回值的信息，请参阅[cl.exe 的返回值](return-value-of-cl-exe.md)。

> [!NOTE]
>  不保证 1024年个字符的命令行输入的限制保持不变的 Windows 的未来版本中。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)
