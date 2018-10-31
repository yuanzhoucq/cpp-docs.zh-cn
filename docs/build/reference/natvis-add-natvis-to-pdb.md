---
title: / NATVIS （将 Natvis 添加到 PDB）
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: 475eb377fd55d6118c109f4e03ea1cf624a563f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446015"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS （将 Natvis 添加到 PDB）

> / NATVIS:*文件名*

## <a name="parameters"></a>参数

*filename*<br/>
要添加到 PDB 文件的 Natvis 文件。 它将 Natvis 文件中的调试器可视化效果嵌入到 PDB 时。

## <a name="remarks"></a>备注

/NATVIS 选项嵌入 Natvis 文件中定义的调试器可视化效果*文件名*到由 LINK 生成的 PDB 文件。 这使调试器能够显示独立于.natvis 文件的可视化效果。 可以使用多个 /NATVIS 选项生成的 PDB 文件中嵌入多个 Natvis 文件。

通过使用不创建 PDB 文件时，链接会忽略 /NATVIS [/debug](../../build/reference/debug-generate-debug-info.md)选项。 有关创建和使用的.natvis 文件的信息，请参阅[Visual Studio 调试器中创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**命令行**中的属性页**链接器**文件夹。

1. /NATVIS 将选项添加到**其他选项**文本框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[在 Visual Studio 调试器中创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)