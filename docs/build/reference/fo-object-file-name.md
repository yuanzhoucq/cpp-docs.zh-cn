---
title: -Fo （对象文件名） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9ab671cbae276796ce89ec12cecbc16334e234e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724229"
---
# <a name="fo-object-file-name"></a>/Fo（对象文件名）

指定对象 (.obj) 文件的名称或要使用的目录，而不是默认目录。

## <a name="syntax"></a>语法

```
/Fopathname
```

## <a name="remarks"></a>备注

如果不使用此选项，该对象文件将使用的源文件和.obj 扩展的基名称。 可以使用任何名称和扩展插件，但推荐的约定是使用。 目标

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击“输出文件”  属性页。

1. 修改**对象文件名**属性。  在开发环境中，对象文件必须具有的扩展。 目标

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>。

## <a name="example"></a>示例

下面的命令行创建对象文件中的现有目录，\OBJECT，驱动器 B.命名 THIS.obj

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>请参阅

[输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)