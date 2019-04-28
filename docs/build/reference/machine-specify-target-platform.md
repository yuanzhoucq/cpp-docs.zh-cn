---
title: /MACHINE（指定目标平台）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
ms.openlocfilehash: e64aa7b2ca9e50ebdc0760f64a9b25e851b45310
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321717"
---
# <a name="machine-specify-target-platform"></a>/MACHINE（指定目标平台）

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>备注

/MACHINE 选项指定程序的目标平台。

通常，您不必指定 /MACHINE 选项。 链接会推断出的.obj 文件中的计算机类型。 但是，在某些情况下，不能确定链接，机类型和问题[链接器工具错误 LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)。 如果发生此类错误，则指定 /MACHINE。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**高级**属性页。

1. 修改**目标计算机**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
