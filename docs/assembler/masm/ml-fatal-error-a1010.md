---
title: ML 错误 A1010
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: eb4d77b856e93a8d64ee6c51bec63ceae59b22e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202060"
---
# <a name="ml-fatal-error-a1010"></a>ML 错误 A1010

**不匹配的块嵌套：**

块开头没有匹配的结束，或块结尾没有匹配的开头。 可能涉及以下项之一：

- 如高级指令[。如果](../../assembler/masm/dot-if.md)， [。重复](../../assembler/masm/dot-repeat.md)，或[。虽然](../../assembler/masm/dot-while.md)。

- 例如一个条件程序集指令[IF](../../assembler/masm/if-masm.md)，[重复](../../assembler/masm/repeat.md)，或**而**。

- 结构或联合定义中。

- 过程定义。

- 段定义。

- 一个[POPCONTEXT](../../assembler/masm/popcontext.md)指令。

- 条件程序集指令，如[ELSE](../../assembler/masm/else-masm.md)， [ELSEIF](../../assembler/masm/elseif-masm.md)，或**ENDIF**没有匹配[如果](../../assembler/masm/if-masm.md)。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>