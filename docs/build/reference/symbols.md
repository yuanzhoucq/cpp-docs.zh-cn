---
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: 4aa6702cfa13523d64553041af4a18270d9babb3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421467"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

此选项显示 COFF 符号表。 符号表存在于所有对象文件。 COFF 符号表将显示的图像文件，仅当使用 /DEBUG 链接。

下面是有关 /SYMBOLS 输出的说明。 可以通过查看在 winnt.h 中的 （IMAGE_SYMBOL 和 IMAGE_AUX_SYMBOL） 或 COFF 文档中找到更多信息的含义的 /SYMBOLS 输出。

对于以下示例转储：

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>备注

符号数字，开头的行的以下说明，介绍列具有与用户相关的信息：

- 第一个三位数字是符号编号。

- 如果第三个列包含段*x*，那一节的对象文件中定义了符号。 但如果 UNDEF 出现，它不定义该对象中，必须在其他位置解析。

- 第五个列 （静态、 外部） 指示符号是否仅在该对象内可见或它是否是公共 (可见外部)。 静态符号 _sym 不会链接到公共符号 _sym;这是两个不同实例的名称为 _sym 函数。

带编号的行中的最后一列是符号名称，修饰名和未修饰名。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)
