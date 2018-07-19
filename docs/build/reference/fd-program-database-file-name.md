---
title: -Fd （程序数据库文件名） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07ab9f1d9c5c611b8da8b19860fe9e0c05351d75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375618"
---
# <a name="fd-program-database-file-name"></a>/Fd（程序数据库文件名）
指定创建的程序数据库 (PDB) 文件的文件名[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
## <a name="syntax"></a>语法  
  
```  
/Fdpathname  
```  
  
## <a name="remarks"></a>备注  
 而无需 **/Fd**，PDB 文件名称默认为 VC*x*0.pdb，其中*x*是在使用 Visual c + + 的主要版本。  
  
 如果指定不包括文件名称 （路径以反斜杠结尾） 的路径名称，编译器将创建一个名为 VC 的.pdb 文件*x*0 指定目录中的 pdb。  
  
 如果指定不包含扩展名的文件名称，编译器将使用作为扩展.pdb。  
  
 此选项还可命名状态 (.idb) 文件用于最小重新生成和增量编译。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击“输出文件”  属性页。  
  
4.  修改**程序数据库文件名**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>。  
  
## <a name="example"></a>示例  
 此命令行创建一个名为 PROG.pdb 和一个名为 PROG.idb 的.idb 文件的.pdb 文件：  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)