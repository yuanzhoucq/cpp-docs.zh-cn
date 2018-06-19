---
title: -Fx （合并插入的代码） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs:
- C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 078019be2a1f818e9dd41acd3db2bced5fbda258
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373863"
---
# <a name="fx-merge-injected-code"></a>/Fx（合并插入的代码）
为每个源文件生成一个副本，使插入的代码合并到源代码。  
  
## <a name="syntax"></a>语法  
  
```  
/Fx  
```  
  
## <a name="remarks"></a>备注  
 为了区分合并的源文件与原始源文件， **/Fx** 将在文件名和文件扩展名之间添加一个 .mrg 扩展名。 例如，一个名为 MyCode.cpp 且包含特性化代码以及由 **/Fx** 生成的文件可创建一个名为 MyCode.mrg.cpp 且包含以下代码的文件：  
  
```  
//+++ Start Injected Code  
[no_injected_text(true)];      // Suppress injected text, it has   
                               // already been injected  
#pragma warning(disable: 4543) // Suppress warnings about skipping   
                               // injected text  
#pragma warning(disable: 4199) // Suppress warnings from attribute   
                               // providers  
//--- End Injected Code  
```  
  
 在 .mrg 文件中，由于某一特性而插入的代码将按以下方式进行分隔：  
  
```  
//+++ Start Injected Code  
...  
//--- End Injected Code  
```  
  
 将 [no_injected_text](../../windows/no-injected-text.md) 特性嵌入在 .mrg 文件中，这允许对 .mrg 文件进行编译而无需重新插入文本。  
  
 应注意的是，.mrg 源文件用于表示由编译器插入的源代码。 .Mrg 文件可能不能完全像原始源文件一样进行编译或运行。  
  
 宏在 .mrg 文件中不展开。  
  
 如果程序包含使用插入的代码的头文件，则 **/Fx** 将为该头生成一个 .mrg.h 文件。 **/Fx** 不会合并不使用插入的代码的头文件。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击“输出文件”  属性页。  
  
4.  修改“展开特性化源”  属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)