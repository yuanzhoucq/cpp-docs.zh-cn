---
title: 描述块
description: NMAKE 使用描述块来关联 makefile 中的目标、依赖项和命令。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322263"
---
# <a name="description-blocks"></a>描述块

描述块构成 makefile 的核心。 它们描述*要创建目标所需的*文件或文件*及其依赖项*。 描述块可能包含*命令*，用于描述如何从依赖项创建目标。 描述块是依赖项行，可选后跟命令块：

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>依赖项行

*依赖项行*指定一个或多个目标，以及零个或多个依赖项。 如果目标不存在，或者时间戳早于从属对象，NMAKE 将执行命令块中的命令。 如果目标是[伪目标](pseudotargets.md)，NMAKE 也会执行命令块。 下面是依赖项行示例：

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

在此依赖项行中`hi_bye.exe`，是目标。 其依赖项是`hello.obj``goodbye.obj`和`helper.lib`。 依赖项`hello.obj`行告诉 NMAKE 在 何时`goodbye.obj`生成目标`helper.lib`，或最近更改比`hi_bye.exe`更改。

目标必须位于行的开头。 它不能缩进与任何空格或选项卡。 使用冒号`:`（ ） 将目标与依赖项分开。 目标、冒号分隔符 （）`:`和依赖项之间允许空格或选项卡。 要拆分依赖项线，请使用目标或从属`\`项之后的反斜杠 （ ）。

在执行命令块之前，NMAKE 会扫描所有依赖项和任何适用的推理规则，以生成*依赖项树*。 依赖项树指定完全更新目标所需的步骤。 NMAKE 会递归地检查从属人本身是否是另一个依赖项列表中的目标。 生成依赖项树后，NMAKE 会检查时间戳。 如果树中的任何从属关系比目标更新，NMAKE 将生成目标。

## <a name="targets"></a><a name="targets"></a>目标

依赖项行的目标部分指定一个或多个目标。 目标可以是任何有效的文件名、目录名称或[伪目标](pseudotargets.md)。 通过使用一个或多个空格或选项卡分隔多个目标。 目标不区分大小写。 允许使用文件名的路径。 目标及其路径不能超过 256 个字符。 如果冒号前面的目标是单个字符，请使用分隔空格。 否则，NMAKE 会将字母冒号组合解释为驱动器指定器。

### <a name="multiple-targets"></a><a name="multiple-targets"></a>多个目标

NMAKE 计算单个依赖项中的多个目标，就像每个目标在单独的描述块中指定一样。

例如，此规则：

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

评估为：

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>累积依赖项

如果重复目标，依赖项在描述块中累积。

例如，这组规则，

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

评估为：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

当单个描述块中的多个依赖项行中有多个目标时，NMAKE 会像在单独的描述块中指定每个目标一样计算它们。 但是，只有最后一个依赖项行中的目标才使用命令块。 NMAKE 尝试对其他目标使用推理规则。

例如，这组规则，

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

评估为：

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>多个描述块中的目标

要使用不同的命令更新多个描述块中的目标，请指定两个连续冒号 （：:)在目标和依赖者之间。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>依赖项副作用

您可以指定具有冒号（:)位于不同位置的两个依赖项行中。 如果命令只出现在其中一行之后，NMAKE 会解释依赖项，就像这些行是相邻的或组合的一样。 它不为没有命令的依赖项调用推理规则。 相反，NMAKE 假定依赖项属于一个描述块，并执行与其他依赖项指定的命令。 请考虑这组规则：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

评估为：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如果使用双冒号 （`::`） ，则不会发生此效果。 例如，这组规则：

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

评估为：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>伪目标

*伪目标*是用于代替依赖项行中的文件名的标签。 它被解释为不存在的文件，因此已经过时。 NMAKE 假定伪目标的时间戳与其所有从属项中的最新时间戳相同。 如果没有依赖变量，则假定当前时间。 如果伪目标用作目标，则始终执行其命令。 用作从属人的伪目标还必须在另一个依赖项中显示为目标。 但是，该依赖项不需要具有命令块。

伪目标名称遵循目标的文件名语法规则。 但是，如果名称没有扩展名，则它可能超过文件名的 8 个字符限制，并且可以长达 256 个字符。

当您希望 NMAKE 自动生成多个目标时，伪目标非常有用。 NMAKE 仅生成命令行上指定的目标。 或者，如果未指定命令行目标，则仅生成 makefile 中第一个依赖项中的第一个目标。 您可以告诉 NMAKE 生成多个目标，而无需在命令行上单独列出它们。 编写包含伪目标的依赖项的描述块，并将要生成的目标列为其依赖项。 然后，首先在 makefile 中放置此描述块，或在 NMAKE 命令行上指定伪目标。

在此示例中，UPDATE 是伪目标。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

计算更新时，NMAKE 将当前目录中的所有文件复制到指定的驱动器和目录。

在下面的 makefile 中，伪`all`目标将`project1.exe`生成`project2.exe`两者`all`，如果命令行上指定了任一目标或未指定目标。 伪目标`setenv`在更新`.exe`文件之前更改 LIB 环境变量：

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>家属

在依赖项行中，使用任何有效的文件名或[伪目标](pseudotargets.md)指定`:`冒号 （`::`） 或双冒号 （ ） 之后的零个或多个从属项。 通过使用一个或多个空格或选项卡分隔多个从属项。 受抚养人不区分大小写。 允许使用文件名的路径。

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>推断的受抚养人

除了在依赖项行中显式列出的依赖项外，NMAKE 可以假定*一个推断的从属项*。 推断的从属关系派生自推理规则，并在显式依赖项之前求计算。 当推断的依赖项与其目标相比过期时，NMAKE 将调用依赖项的命令块。 如果推断的从属关系不存在，或与其自己的从属项相比已经过时，NMAKE 首先更新推断的受抚养项。 有关推断依赖变量的详细信息，请参阅[推理规则](inference-rules.md)。

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>搜索从属人的路径

您可以为每个从属者指定可选的搜索路径。 下面是指定要搜索的目录集的语法：

> *****_目录_\[**;**_目录_...]*****_依赖_

将目录名称封闭在大括号中`{ }`。 使用分号分隔多个目录 。`;` 不允许空格或制表符。 NMAKE 首先在当前目录中查找从属项，然后在指定的顺序中查找目录列表中的从属项。 可以使用宏指定搜索路径的部件或全部。 只有指定的从属者使用此搜索路径。

#### <a name="directory-search-path-example"></a>目录搜索路径示例

此依赖项行演示如何为搜索创建目录规范：

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

目标`reverse.exe`有一个依赖对象`retro.obj`。 大括号内的列表指定两个目录。 NMAKE 首先`retro.obj`在当前目录中搜索。 如果不存在，NMAKE 会搜索`\src\omega`目录，然后搜索`e:\repo\backwards`该目录。

## <a name="see-also"></a>另请参阅

[NMAKE 参考](nmake-reference.md)
