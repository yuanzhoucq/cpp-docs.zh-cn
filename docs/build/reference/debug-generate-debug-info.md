---
title: -DEBUG （生成调试信息） |Microsoft Docs
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
ms.openlocfilehash: 11b3799447e160a56d73441b60215f1dfcb3e227
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132130"
---
# <a name="debug-generate-debug-info"></a>/DEBUG（生成调试信息）
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>备注  

**/Debug**选项创建的可执行文件的调试信息。    
  
链接器的调试信息放在程序数据库 (PDB) 文件。 它会在后续生成的程序的过程更新 PDB。  
  
创建可执行文件 （.exe 文件或 DLL） 用于调试包含名称和相应的 PDB 的路径。 调试器读取嵌入的名称，并使用 PDB 调试程序时。 链接器使用的程序和.pdb 扩展名组成的基名称来命名程序数据库，然后将嵌入已创建时所在的路径。 若要覆盖此默认设置，设置[/PDB](../../build/reference/pdb-use-program-database.md)并指定不同的文件名称。  

**/Debug: fastlink**选项是可用在 Visual Studio 2017 及更高版本。 此选项将使在用于生成可执行文件的各个编译产品私有符号信息。 它将生成对象文件和用于生成而不是进行一套完整的可执行文件的库中的调试信息中建立索引的有限的 PDB。 此选项可以链接两个到四次与完整的 PDB 生成一样快，并且你在本地调试并具有提供的生成产品时，建议使用。 此有限的 PDB 不能用于调试时不可用，如可执行文件在另一台计算机上的部署时所需的生成产品。 在开发人员命令提示符中，您可以使用 mspdbcmf.exe 工具从此有限的 PDB 生成完整的 PDB。 在 Visual Studio 中，使用来生成完整的 PDB 文件的项目或生成菜单项以创建项目或解决方案的完整 PDB。  
  
**/Debug: full**选项将私有符号的所有信息从单个编译产品 （对象文件和库） 都移到单个 PDB，并且可以在链接的最耗时的部分。 但是，可以使用完整的 PDB 调试可执行文件时没有其他生成产品也可用，如可执行文件部署时。  
  
**/Debug： 无**选项不会生成 PDB。  
  
当指定 **/debug**链接器默认为不带任何其他选项 **/debug: full**有关命令行和生成文件生成，为发布生成在 Visual Studio IDE 中，以及调试和发布Visual Studio 2015 及更早版本中的生成。 从 Visual Studio 2017 开始，默认为在 IDE 中的生成系统 **/debug: fastlink**时指定 **/debug**选项对于调试版本。 其他默认值保持不变以保持向后兼容性。  
  
编译器[C7 兼容](../../build/reference/z7-zi-zi-debug-information-format.md)(/ Z7) 选项将使编译器将调试信息保留在.obj 文件。 此外可以使用[程序数据库](../../build/reference/z7-zi-zi-debug-information-format.md)(/Zi) 编译器选项来在.obj 文件的 PDB 中存储的调试信息。 链接器对象的 PDB 首先查找在.obj 文件中写入的绝对路径，然后在目录中包含的.obj 文件。 不能指定对象的 PDB 文件的名称或链接器的位置。  
  
[/ 增量](../../build/reference/incremental-link-incrementally.md)隐式指定 /DEBUG 时。  
  
/ 调试更改的默认值[/opt](../../build/reference/opt-optimizations.md)选项从 REF NOREF 与 ICF NOICF，因此如果你想原始默认值，必须显式指定 /opt: ref 或 /opt: icf。  
  
不能创建.exe 或.dll，其中包含调试信息。 调试信息将始终放入.obj 或.pdb 文件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**调试**属性页。  
  
4.  修改**生成调试信息**属性，以便启用 PDB 生成。 默认情况下，Visual Studio 2017 中，这使 /debug: fastlink。  
  
4.  修改**生成完整程序数据库文件**若要启用用于对每个增量生成完整的 PDB 生成 /debug: full 的属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
