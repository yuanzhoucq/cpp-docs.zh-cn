---
title: /ALIGN （节对齐） |Microsoft 文档
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs:
- C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 543ea30b06f62939f378167d8598c73f66061f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="align-section-alignment"></a>/ALIGN（节对齐）

## <a name="syntax"></a>语法

> **/ALIGN**[**:**_数_]

### <a name="arguments"></a>自变量

*数*  
对齐值以字节为单位。

## <a name="remarks"></a>备注

**/对齐**选项指定程序的线性地址空间中的每个节的对齐方式。 *数*参数是以字节为单位，必须为 2 的幂。 默认值为 4k (4096)。 如果对齐方式生成了无效的图像，则链接器将发出警告。

除非你正在编写之类的设备驱动程序的应用程序，你应该不需要修改对齐方式。

可以修改包含的对齐参数的特定部分的对齐方式[/部分](../../build/reference/section-specify-section-attributes.md)选项。

你指定的对齐方式值不能小于最大的部分对齐。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**框。 选择**确定**或**应用**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)  
