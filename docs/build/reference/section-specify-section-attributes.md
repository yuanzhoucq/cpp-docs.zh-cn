---
title: /SECTION（指定节特性）
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8fb73043c9c185adee0859bb81098eab022430c2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816550"
---
# <a name="section-specify-section-attributes"></a>/SECTION（指定节特性）

> **/SECTION:**_name_,[[**!**]{**DEKPRSW**}][**,ALIGN=**_number_]

## <a name="remarks"></a>备注

**/Section**选项更改的部分中，重写编译节的.obj 文件时设置的属性的属性。

一个*部分*在可移植可执行 (PE) 文件是命名的内存中包含代码或数据连续块。 某些部分包含的代码或数据，您的程序声明，并直接使用，而其他数据部分会为您创建的链接器和库管理器 (lib.exe) 和包含操作系统的重要信息。 有关详细信息，请参阅[PE 格式](/windows/desktop/Debug/pe-format)。

指定一个冒号 （:） 和部分*名称*。 *名称*区分大小写。

因为它们与标准名称冲突，则不使用以下名称。 例如，.sdata RISC 平台上使用：

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

指定一个或多个属性的部分。 下面列出的特性字符不区分大小写。 必须指定你想要具有; 的部分的所有属性省略的属性字符会导致关闭该属性位。 如果未指定 R，W 或 E，现有的读取、 写入或可执行文件的状态将保持不变。

要求反属性，其在字符前加一个感叹号 （！）。 此表中列出的特性字符含义：

|字符|特性|含义|
|---------------|---------------|-------------|
|E|执行|部分是可执行文件|
|R|读取|允许对数据的读取的操作|
|W|Write|允许对数据的写入操作|
|S|Shared|将图像加载的所有进程之间共享该节|
|D|可放弃|将为可丢弃该节标记|
|K|可缓存|将标记为不可缓存的部分|
|P|可分页|将标记为不可分页的部分|

K 和 P 是不寻常的与其对应的部分标志使用相反的含义。 如果您指定其中一个.text 部分通过 **/SECTION:.text，K**选项，没有任何区别，节标记中的在运行时[DUMPBIN](dumpbin-options.md)与[/HEADERS](headers.md)选项;已隐式缓存部分。 若要删除默认值，指定 **/SECTION:.text，！K**相反。 DUMPBIN 显示部分特征，包括"不缓存。"

不具有 E、 R 或 W 设置的 PE 文件中的某个部分可能是无效的。

**ALIGN =**_数_参数允许您指定的特定部分的对齐值。 _数_参数是以字节为单位，必须为 2 的幂。 请参阅[/align](align-section-alignment.md)有关详细信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
