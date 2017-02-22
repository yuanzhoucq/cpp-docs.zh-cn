---
title: "堆栈分配 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 堆栈分配
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函数的 Prolog 负责为局部变量、保存的寄存器、堆栈参数和寄存器参数分配堆栈空间。  
  
 参数区通常位于堆栈底部（即使使用了 alloca），因此在任何函数调用期间，参数区通常与返回地址相邻。  该区域至少包含四项，但通常有足够的空间来保存可能调用的任何函数所需的所有参数。  请注意，即使寄存器参数本身始终不对堆栈进行寻址，也会始终为这些参数分配空间；保证为被调用方的所有参数分配空间。  寄存器参数要求内部地址，这样，如果被调用的函数需要获得参数列表 \(va\_list\) 或单个参数的地址，就会有可用的连续区域。  此区域还提供了一个方便的位置，用于在 thunk 执行期间保存寄存器参数，并可作为一个调试选项（例如，如果参数存储在其 Prolog 代码的内部地址，则在调试期间便易于查找）。  即使被调用函数的参数少于 4 个，该函数实际上也占有这 4 个堆栈位置，并可将这几个位置用于保存参数寄存器值以外的其他目的。  因此，在整个函数调用过程中，调用方不会将信息保存在此堆栈区域中。  
  
 如果在函数中动态分配 \(alloca\) 空间，则必须将非易失寄存器作为帧指针使用，以标记堆栈的固定部分的基址，并且必须在 Prolog 中对该寄存器进行保存和初始化。  请注意，使用 alloca 时，如果同一个调用方对同一个被调用方进行调用，则寄存器参数可能会有不同的内部地址。  
  
 堆栈将始终保持 16 字节对齐，以下两种情况除外：一是在 Prolog 中（例如，推入返回地址之后）；二是在帧函数特定类的 [函数类型](../build/function-types.md) 中指示的位置。  
  
 下面是一个堆栈布局的示例，其中函数 A 调用一个非叶函数 B。  函数 A 的 Prolog 已在栈底为 B 需要的所有寄存器参数和堆栈参数分配了空间。  该调用将返回地址压栈，而 B 的 Prolog 为其局部变量、非易失寄存器分配空间，并为其分配调用函数所需的空间。  如果 B 使用 alloca，则在局部变量\/非易失寄存器保存区与参数堆栈区之间进行空间分配。  
  
 ![AMD 转换示例](../build/media/vcamd_conv_ex_5.png "vcAmd\_conv\_ex\_5")  
  
 当函数 B 调用另一个函数时，正好将返回地址推入 RCX 内部地址的下方。  
  
## 请参阅  
 [堆栈使用](../build/stack-usage.md)