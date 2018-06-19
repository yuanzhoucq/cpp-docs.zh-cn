---
title: '-EP （预处理到 stdout 而无需 #line 指令） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38047fecbbd1bbaa87db3766b046efa8b446d93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375378"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP（不使用 #line 指令预处理到 stdout）
预处理 C 和 c + + 源文件，并将预处理过的文件复制到标准输出设备。  
  
## <a name="syntax"></a>语法  
  
```  
/EP  
```  
  
## <a name="remarks"></a>备注  
 在过程中，所有预处理器指令时，都会执行、 执行宏扩展，并删除注释。 若要保留的预处理输出中的注释，请使用[/C （保留注释预处理期间）](../../build/reference/c-preserve-comments-during-preprocessing.md)选项与 **/EP**。  
  
 **/EP**选项禁止编译。 你必须重新提交编译的预处理过的文件。 **/EP**也会从输出文件禁止显示 **/FA**， **/Fa**，和 **/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列出文件）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
 在更高版本的处理阶段生成错误参考预处理过的文件，而不是原始的源文件的行号。 如果你想要引用的原始源文件行号，使用[/E （预处理到 stdout）](../../build/reference/e-preprocess-to-stdout.md)相反。 **/E**选项会增加`#line`到此目的的输出的指令。  
  
 要与一起发送的预处理的输出`#line`指令，到文件中，使用[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。  
  
 若要使用的预处理的输出发送到 stdout，`#line`指令，使用 **/P**和 **/EP**在一起。  
  
 不能使用具有预编译标头 **/EP**选项。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**预处理器**属性页。  
  
4.  修改**生成预处理文件**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>示例  
 下面的命令行对文件进行预处理`ADD.C`、 保留注释，然后在标准输出设备上显示的结果：  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)