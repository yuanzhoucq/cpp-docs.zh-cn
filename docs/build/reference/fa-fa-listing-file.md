---
title: "/FA、 /Fa （列出文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs: C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0cd569cf16e7b2a14faaa119eacaef0994d09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fa-fa-listing-file"></a>/FA、/Fa（列出文件）
创建包含汇编代码的列表文件。  
  
## <a name="syntax"></a>语法  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/Fa**_路径名_  
  
## <a name="remarks"></a>备注  
`/FA`编译器选项为每个翻译单元中编译，通常对应于 C 或 c + + 源文件生成汇编程序列表文件。 默认情况下，仅汇编程序包含在列表文件中，编码为 ANSI。 可选`c`， `s`，和`u`自变量`/FA`控件是否机器代码或源代码都输出一起列出的汇编和是否列表被编码为 utf-8。  
  
默认情况下，每个列表文件获取与源文件，相同的基名称，并且具有.asm 扩展名。 当使用包括机器代码`c`选项，清单文件的扩展名为.cod。 你可以更改的名称和扩展名的清单文件并创建使用的目录`/Fa`选项。  

### <a name="fa-arguments"></a>/FA 自变量  
无  
仅汇编程序语言包含在列表中。  
  
`c`  
可选。 在列表中包括机器代码。  
  
`s`  
可选。 在列表中包括源代码。  
  
`u`可选。 将编码 utf-8 格式的列表文件并包含字节顺序标记。 默认情况下，文件编码为 ANSI。 使用`u`创建列表文件正确显示在任何系统上，或者如果您正在使用 Unicode 源代码文件作为输入到编译器。  
  
如果这两个`s`和`u`指定，并如果源代码文件使用 Unicode 编码，而不是 utf-8，则.asm 文件中的代码行可能无法正确显示。  
  
### <a name="fa-argument"></a>/Fa 自变量  
无  
一个*源*为每个源代码文件编译中创建.asm 文件。  
  
*filename*列表文件名为*filename*.asm 位于当前目录中。 编译单个源代码文件时，这是仅有效。  
  
*将文件名.扩展名*  
名为的列表文件*文件名.扩展名*位于当前目录中。 编译单个源代码文件时，这是仅有效。  
  
*目录*\  
一个*源文件*创建.asm 文件并将其放在指定*目录*为每个源代码文件编译中。 请注意所需的尾随反斜杠。 允许使用仅在当前的磁盘上的路径。  
  
*目录*\\*filename*列表文件名为*filename*.asm 放在指定*目录*。 编译单个源代码文件时，这是仅有效。  
  
*目录*\\*文件名.扩展名*  
名为的列表文件*文件名.扩展名*放置在指定*目录*。 编译单个源代码文件时，这是仅有效。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  打开**C/c + +**文件夹，然后选择**输出文件**属性页。  
  
3.  修改**汇编程序输出**属性来设置`/FAc`和`/FAs`汇编程序、 计算机和源代码的选项。 修改**使用 Unicode 对于汇编程序列出**属性来设置`/FAu`ANSI 或 utf-8 输出的选项。 修改**ASM 列表位置**设置`/Fa`用于列出文件的名称和位置的选项。  
  
请注意，将设置同时**汇编程序输出**和**使用 Unicode 对于汇编程序列出**属性可能会导致[命令行警告 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)。 若要合并这些选项在 IDE 中的，使用**其他选项**字段**命令行**属性页相反。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>。 若要指定`/FAu`，请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="example"></a>示例  
下面的命令行生成的组合的源和机器代码列表调用 HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)