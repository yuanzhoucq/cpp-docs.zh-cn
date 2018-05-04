---
title: -P （预处理到文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs:
- C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26e9d2d63c7244990a047749f15273b45229c7bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="p-preprocess-to-a-file"></a>/P（预处理到文件）
对 C 和 c + + 源文件进行预处理并预处理的输出写入文件。  
  
## <a name="syntax"></a>语法  
  
```  
/P  
```  
  
## <a name="remarks"></a>备注  
 文件具有相同的基名称作为源文件和一个.i 扩展名。 在过程中，所有预处理器指令时，都会执行、 执行宏扩展，并删除注释。 若要保留的预处理输出中的注释，请使用[/C （保留注释预处理期间）](../../build/reference/c-preserve-comments-during-preprocessing.md)选项和 **/P**。  
  
 **/ P**添加`#line`到输出中的开头和结尾的每个包含的文件以及由预处理器指令进行条件编译删除的行的周围的指令。 这些指令重新编号预处理过的文件的行。 因此，更高版本的处理阶段期间生成的错误是指在原始源文件，而不是预处理过的文件中的行的行号。 若要取消生成的`#line`指令，使用[/EP （不预处理到 stdout #line 指令)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)以及 **/P**。  
  
 **/P**选项禁止编译。 它不会生成.obj 文件中，即使你使用[/Fo （对象文件名）](../../build/reference/fo-object-file-name.md)。 你必须重新提交编译的预处理过的文件。 **/ P**也会从输出文件禁止显示 **/FA**， **/Fa**，和 **/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列出文件）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**预处理器**属性页。  
  
4.  修改**生成预处理文件**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>示例  
 下面的命令行对进行预处理`ADD.C`，保留注释，添加`#line`指令，并将结果写入到一个文件， `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/Fi（预处理输出文件名）](../../build/reference/fi-preprocess-output-file-name.md)