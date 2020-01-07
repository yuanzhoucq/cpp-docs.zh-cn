---
title: ML 非致命错误 A2031
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 4764f7296e28e2128fc4fc80e64f39ceb2a8ed8c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317066"
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

[ML 错误消息](ml-error-messages.md)
