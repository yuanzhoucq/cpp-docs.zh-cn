---
title: FpCsr |Microsoft Docs
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
ms.openlocfilehash: a6ed0500d0382563878d0751ba5386e4cc637fdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718284"
---
# <a name="fpcsr"></a>FpCsr

注册状态还包括 x87 FPU 控制字。 调用约定规定此注册以进行非易失性。

执行程序时的 x87 FPU 控制字寄存器设置为以下的标准值的开头：

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

修改任何 FPCSR 中字段的被调用方必须将它们还原到其调用方返回之前。 此外，已修改任何这些字段的调用方必须将它们还原为其标准值调用被调用方，除非依照约定被调用方需要修改后的值之前。

有两个规则的例外情况的非易失的控制标志：

1. 在函数中的给定函数有案可稽的目的是修改非易失性 FpCsr 其中标志。

1. 如果已经证明更正，这些规则的冲突会导致程序行为/表示其中这些不违反规则，例如，通过全程序分析的程序相同。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)