---
title: ML 错误 A1011 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 843d676cba61e0da5f917a48408e56e79abb9efd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1011"></a>ML 错误 A1011
**指令必须在控制块**  
  
 汇编程序找到其中一个不期望值高级指令。 找到以下指令之一：  
  
-   [.其他](../../assembler/masm/dot-else.md)而无需[。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDIF](../../assembler/masm/dot-endif.md)而无需[。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDW](../../assembler/masm/dot-endw.md)而无需[。WHILE](../../assembler/masm/dot-while.md)  
  
-   [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)而无需[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.继续](../../assembler/masm/dot-continue.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.中断](../../assembler/masm/dot-break.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.其他](../../assembler/masm/dot-else.md)以下 `.ELSE`  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)