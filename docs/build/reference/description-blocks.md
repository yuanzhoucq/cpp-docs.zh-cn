---
title: 描述块
description: NMAKE 使用描述块来关联生成文件中的目标、依赖项和命令。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144534"
---
# <a name="description-blocks"></a>描述块

描述块构成生成文件的核心。 它们描述了创建目标所需的*目标*，即要创建的文件及其*依赖项*。 描述块可以包含一些*命令*，这些命令描述如何从依赖项创建目标。 描述块是一个依赖项行，可选择后跟命令块：

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>依赖项行

*依赖关系行*指定一个或多个目标以及零个或多个依赖项。 如果目标不存在，或具有比依赖项更早的时间戳，NMAKE 将执行命令块中的命令。 如果目标为[伪](pseudotargets.md)目标，NMAKE 还会执行命令块。 下面是一个示例依赖项行：

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

在此依赖项行中，`hi_bye.exe` 是目标。 其依赖项为 `hello.obj`、`goodbye.obj`和 `helper.lib`。 当 `hello.obj`、`goodbye.obj`或 `helper.lib` 的更改比 `hi_bye.exe`最近的更改时，依赖项行将通知 NMAKE 生成目标。

目标必须位于行的开头。 不能将它与任何空格或制表符缩进。 使用冒号（`:`）来分隔目标与从属项。 允许在目标、冒号分隔符（`:`）和从属项之间使用空格或制表符。 若要拆分依赖项行，请在目标或依赖项后使用反斜杠（`\`）。

在执行命令块之前，NMAKE 将扫描所有依赖项和所有适用的推理规则以生成*依赖关系树*。 依赖关系树指定完全更新目标所需的步骤。 NMAKE 递归检查依赖项是否为另一个依赖项列表中的目标。 生成依赖关系树后，NMAKE 检查时间戳。 如果树中的任何依赖项比目标新，NMAKE 将生成目标。

## <a name="targets"></a>目标

依赖项行的目标部分指定一个或多个目标。 目标可以是任何有效的文件名、目录名或[伪](pseudotargets.md)目标。 使用一个或多个空格或制表符分隔多个目标。 目标不区分大小写。 允许使用路径和文件名。 目标及其路径不能超过256个字符。 如果冒号前面的目标是单个字符，请使用分隔的空格。 否则，NMAKE 会将字母冒号组合解释为驱动器说明符。

### <a name="multiple-targets"></a>多个目标

NMAKE 按单个依赖项计算多个目标，就好像每个目标都在单独的描述块中指定的一样。

例如，下面的规则：

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

计算为：

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>累计依赖项

如果重复目标，则在说明块中，依赖关系是累积的。

例如，这组规则，

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

计算为：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如果在单个描述块中有多个依赖行中的多个目标，NMAKE 会对它们进行计算，就好像在单独的描述块中指定了每个目标。 但是，只有最后一个依赖项行中的目标使用命令块。 NMAKE 尝试对其他目标使用推理规则。

例如，这组规则，

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

计算为：

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>多个描述块中的目标

若要使用不同的命令更新多个描述块中的目标，请指定两个连续的冒号（：:)目标和依赖项之间。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>依赖项副作用

可以指定带有冒号的目标（:)在不同位置的两个依赖项行中。 如果命令仅出现在一个行后，NMAKE 会将依赖项解释为相邻或组合的行。 它不会为没有命令的依赖项调用推理规则。 相反，NMAKE 假设依赖项属于一个描述块，并执行与其他依赖项一起指定的命令。 请考虑下面这组规则：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

计算为：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如果使用双冒号（`::`），则不会发生这种情况。 例如，下面的一组规则：

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

计算为：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>伪目标

*伪目标*是用于替代依赖项行中的文件名的标签。 它被解释为不存在的文件，因此过期。 NMAKE 假设伪目标的时间戳与其所有依赖项的最新的时间戳相同。 如果它没有依赖项，则假定为当前时间。 如果将伪目标用作目标，则始终执行其命令。 用作依赖项的伪目标还必须作为另一个依赖项中的目标出现。 但是，该依赖项不需要具有命令块。

伪目标名称遵循目标的文件名语法规则。 但是，如果名称没有扩展名，则它可以超过8个字符的文件名限制，最长可达256个字符。

当你希望 NMAKE 自动构建多个目标时，伪目标非常有用。 NMAKE 仅生成在命令行上指定的目标。 或者，如果未指定命令行目标，它将仅在生成文件的第一个依赖项中生成第一个目标。 可以告诉 NMAKE 构建多个目标，而无需在命令行上单独列出它们。 使用包含伪目标的依赖项编写描述块，并列出要作为依赖项生成的目标。 然后，在生成文件中首先放置此描述块，或在 NMAKE 命令行上指定伪目标。

在此示例中，更新为伪目标。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

计算 UPDATE 时，NMAKE 将当前目录中的所有文件复制到指定的驱动器和目录。

在以下生成文件中，如果在命令行上指定了 `all` 或未指定任何目标，则伪目标 `all` 将同时生成 `project1.exe` 和 `project2.exe`。 在更新 `.exe` 文件之前，伪目标 `setenv` 更改 LIB 环境变量：

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>依赖项

在依赖项行中，使用任意有效的文件名或[伪目标](pseudotargets.md)指定冒号（`:`）或双引号（`::`）后的零个或多个依赖项。 使用一个或多个空格或制表符分隔多个依赖项。 依赖项不区分大小写。 允许使用路径和文件名。

### <a name="inferred-dependents"></a>推理依赖项

除了在依赖项行中显式列出的依赖项，NMAKE 还可以假设*推理依赖*项。 推理依赖项派生自推理规则，并在显式依赖项之前计算。 当推理依赖项与目标的日期过时时，NMAKE 将为依赖项调用命令块。 如果推理依赖项不存在，或与其自己的依赖项相比过期，则 NMAKE 首先更新推理依赖项。 有关推断依赖项的详细信息，请参阅[推理规则](inference-rules.md)。

### <a name="search-paths-for-dependents"></a>依赖项的搜索路径

可以为每个依赖项指定一个可选的搜索路径。 下面是用于指定要搜索的一组目录的语法：

> **{** _directory_\[ **;** _directory_...] **}** _依赖_

将目录名称括在大括号中（`{ }`）。 用分号（`;`）分隔多个目录。 不允许使用空格或制表符。 NMAKE 首先在当前目录中查找依赖项，然后在目录列表中按指定顺序查找依赖项。 您可以使用宏来指定部分或全部搜索路径。 只有指定的依赖项使用此搜索路径。

#### <a name="directory-search-path-example"></a>目录搜索路径示例

此依赖项行显示了如何为搜索创建目录规范：

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

目标 `reverse.exe` 具有一个依赖项，`retro.obj`。 大括号括起的列表指定两个目录。 NMAKE 首先搜索当前目录中的 `retro.obj`。 否则，NMAKE 会搜索 `\src\omega` 目录，然后搜索 `e:\repo\backwards` 目录。

## <a name="see-also"></a>请参阅

[NMAKE 参考](nmake-reference.md)
