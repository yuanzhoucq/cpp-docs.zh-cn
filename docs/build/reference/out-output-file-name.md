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
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812416"
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

此选项.mapfile 或导入的库的默认基名称。 有关详细信息，请参阅[生成映射文件](map-generate-mapfile.md)(/map) 和[/IMPLIB](implib-name-import-library.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**常规**属性页。

1. 修改**输出文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
