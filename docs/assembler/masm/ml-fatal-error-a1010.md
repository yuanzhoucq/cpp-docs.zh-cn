---
title: "ML 错误 A1010 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1010
dev_langs: C++
helpviewer_keywords: A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b495fc2b8bd0e667dd7dae7e23347f6971ec4d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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