---
title: "-Zm （指定预编译标头内存分配限额） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zm
dev_langs:
- C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a45425215fcaf336c0b1630634d0adf37ba3984
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm（指定预编译标头的内存分配限额）
确定编译器分配的用于构造预编译标头的内存量。  
  
## <a name="syntax"></a>语法  
  
```  
/Zmfactor  
```  
  
## <a name="arguments"></a>自变量  
 `factor`  
 一个比例因子，确定编译器用于构造预编译标头的内存量。  
  
 `factor` 参数是编译器定义的工作缓冲区的默认大小所占的百分比。 `factor` 的默认值是 100 (%)，但你可以指定更大或更小的数值。  
  
## <a name="remarks"></a>备注  
 在早期版本的 Visual C++ 中，编译器使用几个离散堆，每个堆都有一定的限制。 当前，编译器可根据需要动态增加堆，最多可增加到总堆大小限制，并且只需要固定大小的缓冲区即可构造预编译标头。 因此， **/Zm**编译器选项很少需要。  
  
 如果编译器用完堆空间，并发出[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)错误消息，当你使用**/Zm**编译器选项，你可能保留了太多内存。 请考虑删除**/Zm**选项。 如果编译器发出[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)错误消息，则伴随[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)消息指定`factor`自变量，则使用重新编译时要使用**/Zm**编译器选项。  
  
 下表显示当你假定默认预编译头缓冲区的大小为 75 MB 时，`factor` 参数如何影响内存分配限制。  
  
|`factor` 的值|内存分配限制|  
|-----------------------|-----------------------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## <a name="other-ways-to-set-the-memory-allocation-limit"></a>设置内存分配限制的其他方式  
  
#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 /Zm 编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在导航窗格中，选择**配置属性**， **C/c + +**，**命令行**。  
  
3.  输入**/Zm**中的编译器选项**其他选项**框。  
  
#### <a name="to-set-the-zm-compiler-option-programmatically"></a>以编程方式设置 /Zm 编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)