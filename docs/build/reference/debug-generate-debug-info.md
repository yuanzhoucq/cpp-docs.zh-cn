---
title: -DEBUG （生成调试信息） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f93c47a0f96cf0b75b453bcea97212d4ab2fd6d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="debug-generate-debug-info"></a>/DEBUG（生成调试信息）
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>备注  

**/调试**选项创建的可执行文件的调试信息。    
  
链接器将调试信息放入程序数据库 (PDB) 文件。 它在程序的后续版本来更新 PDB。  
  
可执行文件 （.exe 文件或 DLL） 创建用于调试包含的名称和相应的 PDB 的路径。 调试器读取嵌入的名称，并使用 PDB，调试程序时。 链接器使用的程序和扩展名为.pdb 的基名称来命名程序数据库中，并将嵌入被创建时所在的路径。 若要覆盖此默认设置，将设置[/PDB](../../build/reference/pdb-use-program-database.md)并指定不同的文件名称。  

**/Debug: fastlink**选项将使在用于生成可执行文件的各个编译产品中的私有符号信息。 它会生成的有限的 PDB，索引中的对象文件和用于生成而不是进行一套完整的可执行文件的库的调试信息。 此选项可以将链接从两个到四次一样快，完整的 PDB 生成，并建议在本地调试和生成产品可用时。 此有限的 PDB 不能用于调试时所需的生成的产品将不可用，如可执行文件在另一台计算机上的部署时。 在开发人员命令提示符下，你可以使用 mspdbcmf.exe 工具从此有限 PDB 生成完整的 PDB。 在 Visual Studio 中，使用用于生成完整的 PDB 文件的项目或生成菜单项来创建项目或解决方案的完整 PDB。  
  
**/DEBUG:FULL**选项将从各个编译产品 （对象文件和库） 的所有私有符号信息移到单个 PDB，并且可以链接的最耗时的一部分。 但是，完整的 PDB 可以用于调试可执行文件不可用时没有其他生成产品，例如当部署的可执行文件。  
  
**/调试： 无**选项不会生成 PDB。  
  
当指定 **/调试**不带任何其他选项，链接器默认为 **/DEBUG:FULL**对于命令行和生成文件生成，对于版本的生成在 Visual Studio IDE，并为调试和发布Visual Studio 2015 及更早版本中的生成。 从 Visual Studio 2017 年 1 开始，在 IDE 中的生成系统默认为 **/debug: fastlink**时指定 **/调试**选项为调试版本。 其他默认值是不变，以保持向后兼容。  
  
编译器的[C7 兼容](../../build/reference/z7-zi-zi-debug-information-format.md)(/ Z7) 选项使编译器将调试信息保留在.obj 文件。 你还可以使用[程序数据库](../../build/reference/z7-zi-zi-debug-information-format.md)(/Zi) 编译器选项来在.obj 文件的 PDB 中存储的调试信息。 链接器查找对象的 PDB 首先在.obj 文件中写入的绝对路径，然后再在目录中，包含.obj 文件。 不能指定对象的 PDB 文件的名称或链接器的位置。  
  
[/ 增量](../../build/reference/incremental-link-incrementally.md)会进行隐式指定 /DEBUG 时。  
  
/ DEBUG 更改的默认值[/选择](../../build/reference/opt-optimizations.md)选项从 REF NOREF 与 ICF NOICF，因此如果你想原始默认值，你必须显式指定 /opt: ref 或 /opt: icf。  
  
不能创建.exe 或.dll，其中包含调试信息。 调试信息始终放置在.obj 或.pdb 文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**调试**属性页。  
  
4.  修改**生成调试信息**属性以启用 PDB 的生成。 在 Visual Studio 2017 默认情况下，这使 /debug: fastlink。  
  
4.  修改**生成完整的程序数据库文件**属性来为每次增量生成完整的 PDB 生成启用 /DEBUG:FULL。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
