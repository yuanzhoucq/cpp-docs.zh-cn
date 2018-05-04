---
title: MxCsr |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9df2225526c20463bdbd618322d031c3245d9493
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="mxcsr"></a>MxCsr
注册状态还包括 MxCsr。 调用约定易失性的部分和非易失性部分中划分此注册。 易失的部分包含的 6 状态标志，MXCSR [0:5]，而的寄存器，MXCSR [6:15]，其余部分被视为非易失性。  
  
 在程序开始执行时，非易失性的部分被设置为以下的标准值：  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 修改任何 MXCSR 中的非易失字段被调用方必须返回到其调用方之前对它们进行还原。 此外，已修改这些字段的任何调用方必须将它们还原为其标准的值在调用被调用方，除非依照约定被调用方需要修改后的值之前。  
  
 有两个例外的非易失的规则的控制标志：  
  
-   在函数中的给定的函数有案可稽的目的是修改非易失性 MxCsr 其中标志。  
  
-   如果已经证明更正这些规则的冲突导致程序行为/意味着其中这些规则未违反，例如，通过全程序分析的程序相同。  
  
 除非专门函数的文档中所述，可以跨函数边界，MXCSR 的易失性部分的状态不进行任何假设。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)