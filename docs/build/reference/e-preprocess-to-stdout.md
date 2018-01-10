---
title: "-E （预处理到 stdout） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /e
dev_langs: C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed083c960421ce17c0ce61036cd05191fc12c797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="e-preprocess-to-stdout"></a>/E（预处理到 stdout）
预处理 C 和 c + + 源文件，并将预处理过的文件复制到标准输出设备。  
  
## <a name="syntax"></a>语法  
  
```  
/E  
```  
  
## <a name="remarks"></a>备注  
 在此过程中，所有预处理器指令时，都会执行、 执行宏扩展，并删除注释。 若要保留的预处理输出中的注释，请使用[/C （保留注释预处理期间）](../../build/reference/c-preserve-comments-during-preprocessing.md)以及编译器选项。  
  
 **/E**添加`#line`对的开头和结尾的每个包含的文件以及周围由预处理器指令进行条件编译删除的行的输出的指令。 这些指令重新编号预处理过的文件的行。 因此，更高版本的处理阶段期间生成的错误是指在原始源文件，而不是预处理过的文件中的行的行号。  
  
 **/E**选项禁止编译。 你必须重新提交编译的预处理过的文件。 **/E**也会从输出文件禁止显示**/FA**， **/Fa**，和**/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列出文件）](../../build/reference/fa-fa-listing-file.md)和[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。  
  
 若要禁止显示`#line`指令，使用[/EP （不预处理到 stdout #line 指令)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)选项。  
  
 预处理的输出发送到的文件而不是为`stdout`，使用[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。  
  
 若要禁止显示`#line`指令和发送经过预处理输出到文件，使用**/P**和**/EP**在一起。  
  
 不能使用具有预编译标头**/E**选项。  
  
 请注意，当预处理到单独的文件时，不在标记后发出空格。 这可导致程序非法或具有意外的副作用。 以下程序在成功进行编译：  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 但是，如果使用进行编译：  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 `int main`在 test2.cpp 不正确地将`intmain`。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  键入中的编译器选项**其他选项**框。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## <a name="example"></a>示例  
 下面的命令行对进行预处理`ADD.C`，保留注释，添加`#line`指令，然后在标准输出设备上显示的结果：  
  
```  
CL /E /C ADD.C  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)