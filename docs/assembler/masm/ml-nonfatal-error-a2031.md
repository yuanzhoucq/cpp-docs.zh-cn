---
title: ML 非致命错误 A2031
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 794fb31fbc22bdefddf9f19e6efcb3c34bbc1861
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431884"
---
# <a name="ml-nonfatal-error-a2031"></a>ML 非致命错误 A2031

**必须是索引或基寄存器**

尝试使用不是内存表达式中的基 / 索引寄存器的寄存器。

例如，以下表达式会导致此错误：

```asm
[ax]
[bl]
```

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>