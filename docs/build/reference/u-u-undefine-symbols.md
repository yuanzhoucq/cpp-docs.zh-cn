---
title: "-U，-u （未定义符号） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18fdaf0c2cb980f1ed19fdfc0577769a9985cf85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="u-u-undefine-symbols"></a>/U、/u（未定义符号）
**/U**编译器选项可取消指定的预处理器符号。 **/U**编译器选项可取消编译器定义的特定于 Microsoft 的符号。  
  
## <a name="syntax"></a>语法  
  
```  
/U[ ]symbol  
/u  
```  
  
## <a name="arguments"></a>自变量  
 `symbol`  
 若要取消定义预处理器符号。  
  
## <a name="remarks"></a>备注  
 既不**/U**或**/u**选项可以取消定义符号通过创建**#define**指令。  
  
 **/U**选项可以取消定义通过使用以前定义的符号**/D**选项。  
  
 默认情况下，编译器定义以下 Microsoft 特定的符号。  
  
|符号|函数|  
|------------|--------------|  
|_CHAR_UNSIGNED|默认 char 类型是无符号。 定义何时[/J](../../build/reference/j-default-char-type-is-unsigned.md)指定选项。|  
|_CPPRTTI|使用代码编译为定义[/GR](../../build/reference/gr-enable-run-time-type-information.md)选项。|  
|_CPPUNWIND|使用代码编译为定义[/EHsc](../../build/reference/eh-exception-handling-model.md)选项。|  
|_DLL|定义何时[/MD](../../build/reference/md-mt-ld-use-run-time-library.md)指定选项。|  
|_M_IX86|默认情况下，为面向 x86 的 600 定义目标。|  
|_MSC_VER|有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。|  
|_WIN32|为 WIN32 应用程序定义。 始终定义。|  
|_MT|定义何时[/MD 或 /MT](../../build/reference/md-mt-ld-use-run-time-library.md)指定选项。|  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**取消定义预处理器定义**或**取消定义所有预处理器定义**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/J (默认 char 类型是无符号)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [/GR （启用运行时类型信息）](../../build/reference/gr-enable-run-time-type-information.md)   
 [/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)   
 [/MD、 /MT、 /LD （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)