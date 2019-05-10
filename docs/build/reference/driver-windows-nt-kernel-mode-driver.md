---
title: /DRIVER（Windows NT 内核模式驱动程序）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: ab7253d7e386bf385bcb3a586c5e0e1c1e860694
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293103"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER（Windows NT 内核模式驱动程序）

>/DRIVER[:UPONLY |:WDM]

## <a name="remarks"></a>备注

使用 **/DRIVER**链接器选项以生成 Windows NT 内核模式驱动程序。

**/DRIVER:UPONLY**导致链接器将添加**IMAGE_FILE_UP_SYSTEM_ONLY**位以指定它是单处理器 (UP) 驱动程序的输出标头中的特征。 操作系统将拒绝加载 UP 驱动程序的多处理器 (MP) 系统上。

**/Driver: wdm**导致链接器设置**IMAGE_DLLCHARACTERISTICS_WDM_DRIVER**位在可选标头的 DllCharacteristics 字段中。

如果 **/DRIVER**未指定，则这些位未设置由链接器。

如果 **/DRIVER**指定：

- **/Fixed: no**生效。 有关详细信息，请参阅 [/FIXED（固定基址）](fixed-fixed-base-address.md)。

- 输出文件的扩展名设置为.sys。 使用 **/out**更改默认的文件名和扩展名。 有关详细信息，请参阅 [/OUT（输出文件名）](out-output-file-name.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**驱动程序**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅[VCLinkerTool.driver 属性](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver)。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
