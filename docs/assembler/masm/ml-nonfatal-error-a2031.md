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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177677"
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