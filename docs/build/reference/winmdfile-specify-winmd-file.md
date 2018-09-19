---
title: -WINMDFILE (指定 winmd 文件) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdea558f1c9a56e68a8e2e61703b92ea569a0629
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709886"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE（指定 winmd 文件）

指定生成的 Windows 运行时元数据 (.winmd) 输出文件的文件名[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)链接器选项。

```
/WINMDFILE:filename
```

## <a name="remarks"></a>备注

使用 `filename` 中指定的值重写默认的 .winmd 文件名 (`binaryname`.winmd)。 请注意，不要将".winmd"追加到`filename`。  如果多个值上列出 **/WINMDFILE**命令行中，最后一个优先。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据文件**框中，输入文件位置。

## <a name="see-also"></a>请参阅

[/WINMD （生成 Windows 元数据）](../../build/reference/winmd-generate-windows-metadata.md)
[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)