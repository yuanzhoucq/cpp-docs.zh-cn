---
title: /FUNCTIONPADMIN （创建可热修补的映像） |Microsoft 文档
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a5ecfcc336e198de0adcc2393f740072d70cae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376749"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN（创建可热修补的映像）

准备要热修补的映像。

## <a name="syntax"></a>语法

> **/FUNCTIONPADMIN**[**:**_space_]  

### <a name="arguments"></a>自变量

*space*<br/>
要将添加到每个函数以字节为单位的开头的填充量。 默认为 5 个填充字节在 x86 和 x64 上这将默认为 6 个字节。 在其他目标上必须提供的值。

## <a name="remarks"></a>备注

为了使链接器以生成可热修补图像，.obj 文件都必须已使用编译[/hotpatch （创建可热修补的映像）](../../build/reference/hotpatch-create-hotpatchable-image.md)。

在编译和链接单次调用 cl.exe，与映像 **/hotpatch**意味着 **/functionpadmin**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/FUNCTIONPADMIN**选项**其他选项**。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
