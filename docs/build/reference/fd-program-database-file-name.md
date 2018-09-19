---
title: -Fd （程序数据库文件名） |Microsoft Docs
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
ms.openlocfilehash: 64e047a832b3c097ced57f9d491b1344c51da495
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724407"
---
# <a name="fd-program-database-file-name"></a>/Fd（程序数据库文件名）

指定创建的程序数据库 (PDB) 文件的文件名[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

## <a name="syntax"></a>语法

```
/Fdpathname
```

## <a name="remarks"></a>备注

无需 **/Fd**，PDB 文件名称默认为 VC*x*0.pdb，其中*x*是 Visual c + + 中使用的主要版本。

如果指定不包括的文件名 （路径以反斜杠结尾） 的路径名称，编译器将创建.pdb 文件，名为 VC*x*0.pdb 指定目录中的。

如果指定不包含扩展名的文件名称，编译器将使用作为扩展.pdb。

此选项还命名用于最小重新生成和增量编译的状态 (.idb) 文件。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击“输出文件”  属性页。

1. 修改**程序数据库文件名**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>。

## <a name="example"></a>示例

此命令行创建一个名为 PROG.pdb 和一个名为 PROG.idb 的.idb 文件的.pdb 文件：

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>请参阅

[输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)