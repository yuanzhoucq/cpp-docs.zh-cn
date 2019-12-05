---
title: ML 非致命错误 A2031
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: f964c67ba7bf399e9a3761e4e201662a6a712a1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856696"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非致命错误 A2031

**必须是索引或基寄存器**

尝试使用的寄存器不是内存表达式中的基寄存器或索引寄存器。

例如，以下表达式将导致此错误：

```asm
[ax]
[bl]
```

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>