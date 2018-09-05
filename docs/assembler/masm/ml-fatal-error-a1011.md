---
title: ML 错误 A1011 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32949773b869d189516a381ca7df941760a1e4e4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690803"
---
# <a name="ml-fatal-error-a1011"></a>ML 错误 A1011

**指令必须是在控制块**

在组装器找到其中一个不期望值的高级别指令。 已找到一个以下指令：

- [.其他](../../assembler/masm/dot-else.md)而无需[。如果](../../assembler/masm/dot-if.md)

- [.ENDIF](../../assembler/masm/dot-endif.md)而无需[。如果](../../assembler/masm/dot-if.md)

- [.ENDW](../../assembler/masm/dot-endw.md)而无需[。WHILE](../../assembler/masm/dot-while.md)

- [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)而无需[。重复](../../assembler/masm/dot-repeat.md)

- [.继续](../../assembler/masm/dot-continue.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)

- [.中断](../../assembler/masm/dot-break.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)

- [.其他](../../assembler/masm/dot-else.md)以下 `.ELSE`

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>