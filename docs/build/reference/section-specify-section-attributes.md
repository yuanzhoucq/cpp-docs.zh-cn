---
title: /SECTION （指定节特性） |Microsoft 文档
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9b0a724f0e9156c81db20bf283e4418dd2f22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379518"
---
# <a name="section-specify-section-attributes"></a>/SECTION（指定节特性）

> **/SECTION:**_名称_，[[**！**]{**DEKPRSW**}] [**，ALIGN =**_数_]

## <a name="remarks"></a>备注

**/部分**选项更改的部分中，重写节的.obj 文件编译时设置的属性的属性。

A*部分*在可移植可执行 (PE) 文件是包含代码或数据的内存的命名连续块。 某些部分包含的代码或程序声明并使用直接，而其他数据部分会为您创建的链接器和库管理器 (lib.exe) 并且包含操作系统的重要信息的数据。 有关详细信息，请参阅[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)。

指定一个冒号 （:） 和部分*名称*。 *名称*区分大小写。

不使用以下名称，因为它们与标准名称发生冲突。 例如，.sdata RISC 平台上使用：

- .arch

- .bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

指定节的一个或多个属性。 下面列出的属性字符不区分大小写。 必须指定你想要有; 的部分的所有属性省略的属性字符会导致关闭该属性位。 如果未指定 R、 W 或 E、 现有的读、 写或可执行文件的状态保持不变。

要求反属性，其在字符前加感叹号 （！）。 此表中显示的属性字符含义：

|字符|特性|含义|
|---------------|---------------|-------------|
|E|执行|部分是可执行文件|
|R|读取|允许对数据进行读的操作|
|W|Write|允许对数据进行写操作|
|S|Shared|加载图像的所有进程之间共享该节|
|D|可丢弃|将为可丢弃该节标记|
|K|可缓存|将节标记为不可缓存：|
|P|可分页|将标记为不可分页的部分|

对应于它们的部分标志可用在负的意义上，K 和 P 并不常用。 如果你指定其中的一个.text 部分使用 **/SECTION:.text、 K**选项，没有任何区别部分标志在运行时[DUMPBIN](../../build/reference/dumpbin-options.md)与[/HEADERS](../../build/reference/headers.md)选项;已隐式缓存部分。 若要删除默认值，指定 **/SECTION:.text，！K**相反。 DUMPBIN 显示部分特征，包括"不缓存。"

没有 E、 R 或 W 设置 PE 文件中的节可能无效。

**ALIGN =**_数_参数允许你指定的特定部分的对齐值。 _数_参数是以字节为单位，必须为 2 的幂。 请参阅[/对齐](../../build/reference/align-section-alignment.md)有关详细信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)  
