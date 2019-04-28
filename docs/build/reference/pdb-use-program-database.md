---
title: /PDB（使用程序数据库）
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320079"
---
# <a name="pdb-use-program-database"></a>/PDB（使用程序数据库）

```
/PDB:filename
```

## <a name="arguments"></a>自变量

*filename*<br/>
链接器将创建程序数据库 (PDB) 的用户指定名称。 它将替换默认名称。

## <a name="remarks"></a>备注

默认情况下，当[/debug](debug-generate-debug-info.md)指定，则链接器将创建包含调试信息的程序数据库 (PDB)。 PDB 的默认文件名称有该程序，扩展名为.pdb 的基名称。

使用 /PDB:*文件名*指定 PDB 文件的名称。 如果未指定 /DEBUG，则忽略 /PDB 选项。

PDB 文件可以是最多为 2 GB。

有关详细信息，请参阅[用作链接器输入的.pdb 文件](dot-pdb-files-as-linker-input.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**调试**属性页。

1. 修改**生成程序数据库文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
