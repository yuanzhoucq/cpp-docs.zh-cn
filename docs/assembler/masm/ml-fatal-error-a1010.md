---
title: ML 错误 A1010
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856873"
---
# <a name="ml-fatal-error-a1010"></a>ML 错误 A1010

**不匹配的块嵌套：**

块开始没有匹配的结尾，或块结束没有匹配的开头。 可能涉及以下内容之一：

- 高级指令，如[。如果](../../assembler/masm/dot-if.md)为，则为[。重复](../../assembler/masm/dot-repeat.md)或[。WHILE](../../assembler/masm/dot-while.md)。

- 条件程序集指令，如[IF](../../assembler/masm/if-masm.md)、 [REPEAT](../../assembler/masm/repeat.md)或**WHILE**。

- 结构或联合定义。

- 过程定义。

- 分段定义。

- [POPCONTEXT](../../assembler/masm/popcontext.md)指令。

- 条件程序集指令，例如[ELSE](../../assembler/masm/else-masm.md)、 [ELSEIF](../../assembler/masm/elseif-masm.md)或**ENDIF** ，无需匹配[IF](../../assembler/masm/if-masm.md)。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>