---
title: /NATVIS（将 Natvis 添加到 PDB）
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: a16e320a2f8f946912fef6a354f27f6514a67e29
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439273"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS（将 Natvis 添加到 PDB）

> /NATVIS：*文件名*

## <a name="parameters"></a>参数

*filename*<br/>
要添加到 PDB 文件中的 Natvis 文件。 它将 Natvis 文件中的调试器可视化效果嵌入 PDB。

## <a name="remarks"></a>备注

/NATVIS 选项将 Natvis 文件*文件名*中定义的调试器可视化效果嵌入到 LINK 生成的 PDB 文件中。 这允许调试器独立于 natvis 文件显示可视化效果。 可以使用多个/NATVIS 选项在生成的 PDB 文件中嵌入多个 Natvis 文件。

当未使用[/debug](debug-generate-debug-info.md)选项创建 PDB 文件时，LINK 将忽略/NATVIS。 有关创建和使用 natvis 文件的信息，请参阅[在 Visual Studio 调试器中创建本机对象的自定义视图](/visualstudio/debugger/create-custom-views-of-native-objects)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**链接器**" 文件夹中的 "**命令行**" 属性页。

1. 将/NATVIS 选项添加到 "**其他选项**" 文本框中。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项没有以编程方式等效的。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
