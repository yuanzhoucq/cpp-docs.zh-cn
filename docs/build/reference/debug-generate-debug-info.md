---
title: /DEBUG（生成调试信息）
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837146"
---
# <a name="debug-generate-debug-info"></a>/DEBUG（生成调试信息）

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>备注

“/DEBUG”选项将为可执行文件创建调试信息。

链接器将调试信息放入程序数据库 (PDB) 文件中。 它会在程序的后续生成期间更新 PDB。

为调试创建的可执行文件（.exe 文件或 DLL）包含相应 PDB 的名称和路径。 调试器可读取嵌入的名称，并在你调试程序时使用 PDB。 链接器使用程序的基名称和扩展名 .pdb 来对程序数据库命名，并嵌入其创建路径。 若要覆盖此默认值，请设置 [/PDB](pdb-use-program-database.md) 并指导其他文件名。

“/DEBUG:FASTLINK”选项在 Visual Studio 2017 及更高版本中提供。 此选项将私有符号信息保留在用于生成可执行文件的单个编译产品中。 它生成一个有限的 PDB，索引到用于生成可执行文件的对象文件和库中的调试信息，而不是生成完整的副本。 此选项的链接速度可以是完整 PDB 生成速度的 2 到 4 倍，建议在本地调试并具有可用的生成产品时使用。 当所需的生成产品不可用时，例如当可执行文件部署在另一台计算机上时，这种有限的 PDB 不能用于调试。 在开发人员命令提示符中，可以使用 mspdbcmf.exe 工具从该有限的 PDB 中生成完整的 PDB。 在 Visual Studio 中，使用“项目”或“生成”菜单项生成完整的 PDB 文件，以便为项目或解决方案创建完整的 PDB。

“/DEBUG:FULL”选项可将所有私有符号信息从单个编译产品（对象文件和库）移动到单个 PDB 中，并且是链接中最耗时的部分。 但是，没有其他可用的生成产品时，例如部署可执行文件时，完整的 PDB 可用于调试可执行文件。

“/DEBUG:NONE”选项不会生成 PDB。

指定“/DEBUG”而不包含其他选项时，链接器默认为“/DEBUG:FULL”，可用于命令行和生成文件生成、Visual Studio IDE 中的发布生成，以及 Visual Studio 2015 及早期版本中的调试和发布生成。 从 Visual Studio 2017 开始，指定调试版本的“/DEBUG”选项时，IDE 中的生成系统默认为“/DEBUG:FASTLINK”。 其他默认值保持不变以保持向后兼容性。

编译器的 [C7 兼容](z7-zi-zi-debug-information-format.md) (/Z7) 选项会使编译器将调试信息保留在 .obj 文件中。 还可以使用[程序数据库](z7-zi-zi-debug-information-format.md) (/Zi) 编译器选项，以将调试信息存储在 .obj 文件的 PDB 中。 链接器首先在 .obj 文件中编写的绝对路径中查找对象的 PDB，然后在包含 .obj 文件的目录中查找。 无法为链接器指定对象的 PDB 文件名或位置。

指定 /DEBUG 时隐式使用 [/INCREMENTAL](incremental-link-incrementally.md)。

/DEBUG 将 [/OPT](opt-optimizations.md) 选项的默认值从 REF 更改为 NOREF 以及从 ICF 更改为 NOICF，如果想要初始默认值，必须显式指定 /OPT:REF 或 /OPT:ICF。

不能创建包含调试信息的 .exe 或 .dll。 调试信息将始终放置在 .obj 或 .pdb 文件中。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击“链接器”文件夹。

1. 单击“调试”属性页。

1. 修改“生成调试信息”属性，以启用 PDB 生成。 这将默认在 Visual Studio 2017 及更高版本中启用 /DEBUG:FASTLINK。

1. 修改“生成完成的程序数据库文件”属性，以启用 /DEBUG:FULL，针对每个增量生成进行完整的 PDB 生成。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
