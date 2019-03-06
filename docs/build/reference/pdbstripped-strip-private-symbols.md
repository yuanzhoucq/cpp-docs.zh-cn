---
title: /PDBSTRIPPED（去除私有符号）
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: c0a79eb8d1c00be2b855ec08ffe44f4e7d7a2e05
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412622"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED（去除私有符号）

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>自变量

*pdb_file_name*<br/>
链接器将创建去除的程序数据库 (PDB) 的用户指定名称。

## <a name="remarks"></a>备注

在生成程序图像与任何编译器或链接器生成的 PDB 文件的选项时，/PDBSTRIPPED 选项将创建第二个程序数据库 (PDB) 文件 ([/debug](../../build/reference/debug-generate-debug-info.md)， [/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，/Zd 或 /Zi)。 此 PDB 文件省略您不希望交付给客户的符号。 第二个 PDB 文件将仅包含：

- 公共符号

- 对象文件和它们参与构成的可执行文件的部分的列表

- 用于遍历堆栈帧指针优化 (FPO) 调试记录

去除的 PDB 文件将包含：

- 类型信息

- 行号信息

- 例如，用于函数、 局部变量和静态数据的每个对象文件 CodeView 符号

当使用 /PDBSTRIPPED 时，仍将生成完整的 PDB 文件。

如果没有创建 PDB 文件，则忽略 /PDBSTRIPPED。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**调试**属性页。

1. 修改**去除私有符号**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
