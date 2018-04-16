---
title: -驱动程序 （Windows NT 内核模式驱动程序） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29234e3c0e368c7710f9071c753422bc4e6ef2b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER（Windows NT 内核模式驱动程序）

>/ 驱动程序 [: UPONLY |: WDM]

## <a name="remarks"></a>备注

使用**/DRIVER**链接器选项生成 Windows NT 内核模式驱动程序。

**/DRIVER:UPONLY**导致链接器添加**IMAGE_FILE_UP_SYSTEM_ONLY**位与输出标头以指定它是单处理器 （向上） 驱动程序中的特征。 系统将拒绝加载 UP 驱动程序的多处理器 (MP) 系统上。

**/DRIVER:WDM**导致链接器设置**IMAGE_DLLCHARACTERISTICS_WDM_DRIVER**位可选标头的 DllCharacteristics 字段中。

如果**/DRIVER**未指定，则链接器不设置这些位。

如果**/DRIVER**指定：

- **/Fixed: no**生效。 有关详细信息，请参阅 [/FIXED（固定基址）](../../build/reference/fixed-fixed-base-address.md)。

- 输出文件的扩展名设置为.sys。 使用**/out**更改默认的文件名和扩展名。 有关详细信息，请参阅 [/OUT（输出文件名）](../../build/reference/out-output-file-name.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**驱动程序**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅[VCLinkerTool.driver 属性](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver)。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)   
[链接器选项](../../build/reference/linker-options.md)
