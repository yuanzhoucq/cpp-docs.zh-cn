---
title: 针对旧代码的浮点支持 (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509638"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>针对旧代码的浮点支持 (Visual C++)

MMX 和浮点堆栈寄存器 (MM0-MM7/ST0-ST7) 会保留在上下文切换。  没有这些寄存器显式调用约定。  使用这些寄存器严格禁止在内核模式代码。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)