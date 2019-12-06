---
title: ML 错误 A1011
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856847"
---
# <a name="ml-fatal-error-a1011"></a>ML 错误 A1011

**指令必须在控制块中**

组装器找到了不需要的高级指令。 找到以下指令之一：

- [.否则](../../assembler/masm/dot-else.md)，则为[。如果](../../assembler/masm/dot-if.md)

- [.ENDIF](../../assembler/masm/dot-endif.md) [，无。如果](../../assembler/masm/dot-if.md)

- [..ENDW](../../assembler/masm/dot-endw.md) （不含） [。WHILE](../../assembler/masm/dot-while.md)

- [..UNTILCXZ](../../assembler/masm/dot-untilcxz.md) （不含） [。重复](../../assembler/masm/dot-repeat.md)

- [.](../../assembler/masm/dot-continue.md)不继续[。WHILE](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)

- [.](../../assembler/masm/dot-break.md)不带[的分行符。WHILE](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)

- [.否则](../../assembler/masm/dot-else.md)`.ELSE`

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>