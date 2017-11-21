---
title: "堆栈 （堆栈分配） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
dev_langs: C++
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e44c9920e2725bc70d3b8abe385b94961486e945
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="stack-stack-allocations"></a>/STACK（堆栈分配）
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>备注  
 /STACK 选项以字节为单位设置堆栈大小。 仅当你生成的.exe 文件时，请使用此选项。  
  
 `reserve`值指定的总堆栈分配虚拟内存中。 对于 ARM、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 计算机，默认堆栈大小为 1 MB。  
  
 `commit`受到操作系统的解释。 在 Windows RT 中，它指定一次性分配的物理内存量。 提交的虚拟内存后，要分页文件中保留的空间。 当应用程序需要更多堆栈空间时，增大 `commit` 值可以节省时间，但会增加内存需求并可能延长启动时间。 对于 ARM、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 计算机，默认提交值为 4 KB。  
  
 以十进制或 C 语言表示方式指定 `reserve` 和 `commit` 值。  
  
 设置堆栈大小另一个方法是使用[STACKSIZE](../../build/reference/stacksize.md)模块定义 (.def) 文件中的语句。 **STACKSIZE**替代堆栈分配 （/ 堆栈） 如果同时指定了选项。 你可以使用生成的.exe 文件后更改的堆栈大小[EDITBIN](../../build/reference/editbin-reference.md)工具。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**系统**属性页。  
  
4.  修改以下属性之一：  
  
    -   **堆栈提交大小**  
  
    -   **堆栈保留大小**  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 属性。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)