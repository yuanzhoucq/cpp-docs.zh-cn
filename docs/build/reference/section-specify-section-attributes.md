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
ms.openlocfilehash: 0a52e9c9dcd53b01f17dc36825732b34771c75bb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492630"
---
# <a name="section-specify-section-attributes"></a>/SECTION（指定节特性）

> **/SECTION:** _name_、[[ **!** ]{**DEKPRSW**}][ **, ALIGN =** _number_]

## <a name="remarks"></a>备注

**/SECTION**选项将更改节的特性, 重写编译节的 .obj 文件时设置的特性。

可移植可执行 (PE) 文件中的*部分*是包含代码或数据的已命名的连续内存块。 有些部分包含程序声明并直接使用的代码或数据, 而其他数据节是通过链接器和库管理器 (.lib) 为你创建的, 并且包含对操作系统至关重要的信息。 有关详细信息, 请参阅[PE 格式](/windows/win32/Debug/pe-format)。

指定冒号 (:)和节*名称*。 该*名称*区分大小写。

不要使用以下名称, 因为它们与标准名称冲突。 例如, .sdata 平台上使用了 .sdata:

- . 拱

- .bss

- 。数据

- .edata

- .idata

- .pdata

- 。 rdata

- 。 .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

指定节的一个或多个属性。 下面列出的属性字符不区分大小写。 您必须指定您希望此部分具有的所有属性;省略的属性字符会导致关闭属性位。 如果未指定 R、W 或 E, 则现有的 "读取"、"写入" 或 "可执行" 状态将保持不变。

若要对某个属性求反, 请在其字符前面加上一个惊叹号 (!)。 此表显示了属性字符的含义:

|字符|特性|含义|
|---------------|---------------|-------------|
|E|执行|该部分是可执行文件|
|R|读取|允许对数据进行读操作|
|W|Write|允许对数据进行写操作|
|S|Shared|共享所有加载映像的进程中的节|
|D|可放弃|将节标记为可放弃|
|K|缓存|将该节标记为不可缓存|
|P|可|将节标记为不可分页|

K 和 P 非常罕见, 因为在消极意义上使用与它们相对应的部分标志。 如果通过使用 **/SECTION:. text, K**选项在. text 部分指定其中一个选项, 则使用[/HEADERS](headers.md)选项运行[DUMPBIN](dumpbin-options.md)时, 部分标志没有差别;已隐式缓存该部分。 若要删除默认值, 请指定 **/SECTION: text!K** 。 DUMPBIN 显示部分特征, 包括 "未缓存"。

PE 文件中没有设置 E、R 或 W 的部分可能无效。

**ALIGN =** _number_参数可为特定节指定对齐值。 _Number_参数以字节为单位, 必须是2的幂。 有关详细信息, 请参阅[/align](align-section-alignment.md) 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入选项。 选择 **"确定" 或 "** **应用**" 以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
