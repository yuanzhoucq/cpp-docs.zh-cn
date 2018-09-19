---
title: MxCsr |Microsoft Docs
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
ms.openlocfilehash: 0d18a4247d36e6894230d74322d52cd5854e42fb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726500"
---
# <a name="mxcsr"></a>MxCsr

注册状态还包括 MxCsr。 调用约定将此寄存器划分为易失性的部分而非易失性的部分。 易失性部分由 6 种状态标志 MXCSR [0:5]，而其余的寄存器，MXCSR [6:15] 被视为非易失性。

在程序执行的开始处的非易失性的部分设置为以下的标准值：

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

修改的任何非易失性 MXCSR 中字段的被调用方必须将它们还原到其调用方返回之前。 此外，已修改任何这些字段的调用方必须将它们还原为其标准值调用被调用方，除非依照约定被调用方需要修改后的值之前。

有两个规则的例外情况的非易失的控制标志：

- 在函数中的给定函数有案可稽的目的是修改非易失性 MxCsr 其中标志。

- 如果已经证明更正，这些规则的冲突会导致程序行为/表示其中这些不违反规则，例如，通过全程序分析的程序相同。

除非专门函数的文档中所述，可以跨函数边界的可变部分的 MXCSR 状态不进行任何假设。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)