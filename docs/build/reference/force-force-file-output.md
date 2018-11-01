---
title: /FORCE（强制文件输出）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: 5555a76cc792c15bea9c6c393debbd0fb38e30e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445651"
---
# <a name="force-force-file-output"></a>/FORCE（强制文件输出）

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>备注

/FORCE 选项告知链接器创建有效的.exe 文件或 DLL 即使而不是引用的符号定义或多次定义。

/FORCE 选项可以采用一个可选参数：

- 使用 /force： 若要创建的输出文件，不管是否链接找到多个符号的定义。

- 使用 /FORCE: UNRESOLVED 可创建输出文件，不管是否链接找到未定义的符号。 / 强制： 无法解析未解析入口点符号是否忽略。

/ 强制不带任何参数表示多次定义和未解决的。

使用此选项创建的文件可能不会按预期运行。 指定 /FORCE 选项时，链接器将不会以增量方式链接。

如果使用编译的模块 **/clr**， **/force**将不会创建映像。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 点击“命令行”  属性页。

1. 该选项键入**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)