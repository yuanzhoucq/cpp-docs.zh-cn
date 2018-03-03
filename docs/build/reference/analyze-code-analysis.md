---
title: "-分析 （代码分析） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba76ddd10866e414d9817f628c7a1aec019964de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="analyze-code-analysis"></a>/analyze（代码分析）
启用代码分析和控制选项。  
  
## <a name="syntax"></a>语法  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## <a name="arguments"></a>自变量  
 /analyze  
 在默认模式下打开分析。 分析输出转到**输出**与其他错误信息类似的窗口。 使用**/ 分析-**来显式关闭分析。  
  
 /analyze:WX-  
 指定**/ 分析： WX-**意味着代码分析警告不被视为错误使用编译时**/WX**。 有关详细信息，请参阅 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX（警告级别）](../../build/reference/compiler-option-warning-level.md)。  
  
 /analyze:log `filename`  
 将详细的分析器结果作为 XML 写入由 `filename` 指定的文件。  
  
 /analyze:quiet  
 关闭到的分析器输出**输出**窗口。  
  
 /analyze:stacksize `number`  
 `number`与此选项一起使用的参数指定的大小，以字节为单位的警告的堆栈帧[C6262](/visualstudio/code-quality/c6262)生成。 如果未指定此参数，则默认情况下堆栈帧的大小为 16KB。  
  
 /analyze:max_paths `number`  
 用于此选项的 `number` 参数指定要分析的代码路径的最大数目。 如果未指定此参数，则默认情况下此数目为 256。 值越大，执行的检查越彻底，但分析时间可能会更长。  
  
 /analyze:only  
 通常，编译器在运行分析器后会生成代码并执行更多语法检查。 **/ 分析： 仅**选项将关闭此代码生成传递; 这会使分析速度更快，但不是会发出编译错误和警告已由编译器的代码生成传递发现。 如果程序存在代码生成错误，则分析结果可能不可靠；因此，建议你只有在代码已传递代码生成语法检查且没有错误时才使用此选项。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[的代码分析 C/c + + 概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[的代码分析 C/c + + 警告](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**代码分析**节点。  
  
4.  选择 **“常规”** 属性页。  
  
5.  修改一个或多个**代码分析**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)