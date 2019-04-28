---
title: /WINMDFILE（指定 winmd 文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5d24d1d1aad8442f549dcb1aa4bd6414070c282c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316478"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE（指定 winmd 文件）

指定生成的 Windows 运行时元数据 (.winmd) 输出文件的文件名[/WINMD](winmd-generate-windows-metadata.md)链接器选项。

```
/WINMDFILE:filename
```

## <a name="remarks"></a>备注

使用 `filename` 中指定的值重写默认的 .winmd 文件名 (`binaryname`.winmd)。 请注意，不要将".winmd"追加到`filename`。  如果多个值上列出 **/WINMDFILE**命令行中，最后一个优先。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**Windows 元数据**属性页。

1. 在中**Windows 元数据文件**框中，输入文件位置。

## <a name="see-also"></a>请参阅

[/WINMD（生成 Windows 元数据）](winmd-generate-windows-metadata.md)<br/>
[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
