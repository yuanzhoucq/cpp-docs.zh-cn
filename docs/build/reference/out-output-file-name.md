---
title: /OUT（输出文件名）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: f5ba323b830b9d06956d88d957206e3f73c15418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497167"
---
# <a name="out-output-file-name"></a>/OUT（输出文件名）

```
/OUT:filename
```

## <a name="arguments"></a>自变量

*filename*<br/>
输出文件的用户指定名称。 它将替换默认名称。

## <a name="remarks"></a>备注

/OUT 选项重写的默认名称和链接器将创建程序的位置。

默认情况下，链接器窗体使用指定的第一个.obj 文件和相应的扩展插件 （.exe 或.dll） 的基名称的文件名称。

此选项.mapfile 或导入的库的默认基名称。 有关详细信息，请参阅[生成映射文件](../../build/reference/map-generate-mapfile.md)(/map) 和[/IMPLIB](../../build/reference/implib-name-import-library.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**常规**属性页。

1. 修改**输出文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)