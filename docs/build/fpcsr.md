---
title: FpCsr |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9defb41a026b32acb4375185f14c903788b91a23
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367441"
---
# <a name="fpcsr"></a>FpCsr
注册状态还包括 x87 FPU 控制字。 调用约定决定此寄存器是非非易失性。  
  
 执行程序时的 x87 FPU 控制字寄存器设置为以下的标准值的开头：  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 修改任何 FPCSR 中字段的被调用方必须之前将它们还原到其调用方返回。 此外，已修改这些字段的任何调用方必须将它们还原为其标准的值在调用被调用方，除非依照约定被调用方需要修改后的值之前。  
  
 有两个例外的非易失的规则的控制标志：  
  
1.  在函数中的给定的函数有案可稽的目的是修改非易失性 FpCsr 其中标志。  
  
2.  如果已经证明更正这些规则的冲突导致程序行为/意味着其中这些规则未违反，例如，通过全程序分析的程序相同。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)