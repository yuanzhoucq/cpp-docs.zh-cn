---
title: ML 错误 A1010 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b622595b6994c4c4eaa74ed8f824f28dffe89b1a
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1010"></a>ML 错误 A1010
**不匹配的块嵌套：**  
  
 开头的块没有匹配的结束，或块结束没有匹配的开头。 下列情况之一可能会涉及到：  
  
-   如高级指令[。如果](../../assembler/masm/dot-if.md)， [。重复](../../assembler/masm/dot-repeat.md)，或[。虽然](../../assembler/masm/dot-while.md)。  
  
-   如条件程序集指令[如果](../../assembler/masm/if-masm.md)，[重复](../../assembler/masm/repeat.md)，或**时**。  
  
-   结构或联合定义中。  
  
-   过程定义。  
  
-   段定义。  
  
-   A [POPCONTEXT](../../assembler/masm/popcontext.md)指令。  
  
-   条件程序集指令，如[ELSE](../../assembler/masm/else-masm.md)， [ELSEIF](../../assembler/masm/elseif-masm.md)，或**ENDIF**没有与其匹配的[如果](../../assembler/masm/if-masm.md)。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)