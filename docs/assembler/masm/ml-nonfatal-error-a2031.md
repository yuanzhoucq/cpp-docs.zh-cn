---
title: ML 非致命错误 A2031 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf6744224847e114e76df6e7ad6470696d3e8387
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682653"
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