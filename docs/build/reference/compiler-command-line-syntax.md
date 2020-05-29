---
title: MSVC 编译器命令行语法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320549"
---
# <a name="compiler-command-line-syntax"></a>编译器命令行语法

CL 命令行使用以下语法：

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

下表描述了对 CL 命令的输入。

|条目|含义|
|-----------|-------------|
|*选项*|一个或多个[CL 选项](compiler-options.md)。 请注意，所有选项都适用于所有指定的源文件。 选项由前斜杠 （/） 或破折号 （-） 指定。 如果选项采用参数，则该选项的说明将记录选项和参数之间是否允许空格。 选项名称（/HELP 选项除外）区分大小写。 有关详细信息[，请参阅 CL 选项的顺序](order-of-cl-options.md)。|
|`file`|一个或多个源文件、.obj 文件或库的名称。 CL 编译源文件并将 .obj 文件和库的名称传递给链接器。 有关详细信息[，请参阅 CL 文件名语法](cl-filename-syntax.md)。|
|*自由*|一个或多个库名称。 CL 将这些名称传递给链接器。|
|*命令文件*|包含多个选项和文件名的文件。 有关详细信息，请参阅[CL 命令文件](cl-command-files.md)。|
|*链接选择*|一个或多个[MSVC 链接器选项](linker-options.md)。 CL 将这些选项传递给链接器。|

只要命令行上的字符数不超过 1024，即操作系统规定的限制，就可以指定任意数量的选项、文件名和库名。

有关 cl.exe 的返回值的信息，请参阅[cl.exe 的返回值](return-value-of-cl-exe.md)。

> [!NOTE]
> 在 Windows 的未来版本中，不能保证 1024 个字符的命令行输入限制保持不变。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)
