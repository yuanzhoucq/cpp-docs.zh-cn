---
title: /WINMDFILE（指定 winmd 文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5532046f4284100c60bb82c12b4d47c721fc275e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413077"
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

[/WINMD（生成 Windows 元数据）](../../build/reference/winmd-generate-windows-metadata.md)<br/>
[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
