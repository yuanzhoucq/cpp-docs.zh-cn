---
title: -/Qvec-report （自动向量化报告等级） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43c9a182046ff148621151107a98932cc39835f2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report（自动矢量化程序报告等级）
启用编译器的报告功能[自动向量化](../../parallel/auto-parallelization-and-auto-vectorization.md)并在编译期间指定的输出信息性消息的级别。  
  
## <a name="syntax"></a>语法  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>备注  
 **/ Qvec-报表： 1**  
 输出向量化的循环条信息性消息。  
  
 **/ Qvec-报表： 2**  
 输出信息性消息的向量化的循环和 for 循环未向量化以及原因代码。  
  
 有关原因代码和消息的信息，请参阅[矢量化程序和并行化程序消息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /Qvec-report 编译器选项  
  
1.  在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。  
  
2.  在**属性页**对话框中，在**C/c + +**，选择**命令行**。  
  
3.  在**其他选项**框中，输入`/Qvec-report:1`或`/Qvec-report:2`。  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>以编程方式设置 /Qvec-report 编译器选项  
  
-   使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的代码示例。  
  
## <a name="see-also"></a>请参阅  
 [/Q 选项 （低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [本机代码中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=263662)