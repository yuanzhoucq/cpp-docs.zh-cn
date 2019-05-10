---
title: /FUNCTIONPADMIN（创建可热修补的映像）
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292388"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN（创建可热修补的映像）

准备映像进行热修补。

## <a name="syntax"></a>语法

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>自变量

*space*<br/>
要添加到的以字节为单位的每个函数开头的填充量。 在 x86 上此值默认为 5 个字节的填充和 x64 上此值默认为 6 个字节。 在其他目标上必须提供一个值。

## <a name="remarks"></a>备注

为了使链接器以生成可热修补映像，.obj 文件必须具有已编译[/hotpatch （创建可热修补映像）](hotpatch-create-hotpatchable-image.md)。

编译和链接的单次调用的 cl.exe，与映像时 **/hotpatch**意味着 **/functionpadmin**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/FUNCTIONPADMIN**选项**其他选项**。 选择“确定”以保存更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
