---
title: ML 非致命错误 A2085
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3bd89fb2b7f8b755cdb095e63ed89386332ecf9d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855753"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非致命错误 A2085

**当前 CPU 模式下未接受的指令或寄存器**

尝试使用的指令、寄存器或关键字对于当前处理器模式无效。

例如，32位寄存器需要[386](../../assembler/masm/dot-386.md)或更高版本。 控制寄存器（如 CR0）需要特权模式[。 .386p](../../assembler/masm/dot-386p.md)或更高版本。 还将为需要的**NEAR32**、 **FAR32**和**平面**关键字生成此错误。**386**或更高版本。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>