---
title: ML 非致命错误 A2085
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 729f6f38761171c6ddc4cccfc2443c6a2b597bf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444348"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非致命错误 A2085

**指令或不接受当前 CPU 模式下的注册**

尝试使用指令、 寄存器或对当前处理器模式下无效的关键字。

例如，需要 32 位寄存器[.386](../../assembler/masm/dot-386.md)或更高版本。 如 CR0 需要特权模式下，控制寄存器[.386P](../../assembler/masm/dot-386p.md)或更高版本。 此错误也会生成有关**NEAR32**， **FAR32**，并**平面**要求的关键字。**386**或更高版本。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>