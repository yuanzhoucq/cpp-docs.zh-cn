---
title: /RELEASE（设置校验和）
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: 1dc09b38beeb763733f8fa6a8ffa972059b30e03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318922"
---
# <a name="release-set-the-checksum"></a>/RELEASE（设置校验和）

```
/RELEASE
```

## <a name="remarks"></a>备注

/RELEASE 选项的.exe 文件头中设置校验和。

操作系统要求的设备驱动程序的校验和。 设置发布版本的设备驱动程序的校验和，以确保与将来的操作系统的兼容性。

默认情况下设置 /RELEASE 选项时[已](subsystem-specify-subsystem.md)指定选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**高级**属性页。

1. 修改**设置校验和**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
