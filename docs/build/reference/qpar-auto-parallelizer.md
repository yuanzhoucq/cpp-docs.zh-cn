---
title: -Qpar （自动并行化程序） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c3501422a0bfbaba8aea0e45c102f63948b7db
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684500"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar（自动并行化程序）
使[自动并行化程序](../../parallel/auto-parallelization-and-auto-vectorization.md)编译器自动并行化代码中的循环功能。  
  
## <a name="syntax"></a>语法  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>备注  
 当编译器自动并行化代码中的循环时，它会将计算分布在多个处理器内核中。 仅当编译器确定将循环并行化合法时，才会执行此操作，并且并行化会提高性能。  
  
 提供了 `#pragma loop()` 指令来帮助优化程序并行化特定循环。 有关详细信息，请参阅[循环](../../preprocessor/loop.md)。  
  
 有关如何启用自动并行化程序的输出消息的信息，请参阅[/Qpar-report （自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)。  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Qpar 编译器选项  
  
1.  在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。  
  
2.  在中**属性页**对话框中的**C/c + +**，选择**命令行**。  
  
3.  在中**其他选项**框中，输入`/Qpar`。  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>以编程方式设置 /Qpar 编译器选项  
  
-   使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。  
  
## <a name="see-also"></a>请参阅  
 [/Q 选项 （低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [/Qpar-report （自动并行化程序报告等级）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [#pragma loop （)](../../preprocessor/loop.md)   
 [本机代码中的并行编程](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)